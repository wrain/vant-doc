<template>
  <div :class="['van-doc-content', `van-doc-content--${currentPage}`]">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'van-doc-content',

  computed: {
    currentPage() {
      const { path } = this.$route;
      if (path) {
        return path.split('/').slice(-1)[0];
      }
      return this.$route.name;
    }
  }
};
</script>

<style lang="postcss">
@import '../style/variable';

.van-doc-content {
  flex: 1;
  position: relative;
  padding: 0 0 75px;

  .card {
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 6px;
    background-color: #fff;
    box-shadow: 0 8px 12px #ebedf0;
  }

  a {
    color: $van-doc-blue;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    line-height: 1.5;
    font-weight: normal;
    color: $van-doc-black;
  }

  h1 {
    margin: 0 0 30px;
    font-size: 30px;
  }

  h2 {
    font-size: 22px;
    margin: 45px 0 20px;
  }

  h3 {
    font-size: 17px;
    font-weight: 500;
    margin-bottom: 12px;
  }

  h4,
  h5 {
    font-size: 14px;
    margin: 12px 0;
  }

  p {
    font-size: 14px;
    line-height: 26px;
    color: $van-doc-text-color;
  }

  table {
    width: 100%;
    margin-top: 12px;
    font-size: 13px;
    line-height: 1.5;
    border-radius: 6px;
    border-collapse: collapse;
    color: $van-doc-text-color;

    th {
      padding: 8px 10px;
      text-align: left;
      font-weight: 500;

      &:first-child {
        padding-left: 0;
      }

      &:last-child {
        padding-right: 0;
      }
    }

    td {
      padding: 8px;
      border-top: 1px solid $van-doc-code-background-color;

      &:first-child {
        padding-left: 0;
      }

      &:last-child {
        padding-right: 0;
      }
    }

    code {
      font-size: 13px;
      padding: 0 8px;
      font-family: inherit;
      word-break: keep-all;
    }
  }

  ul li,
  ol li {
    color: $van-doc-text-color;
    font-size: 14px;
    line-height: 22px;
    margin: 5px 0 5px 10px;
    padding-left: 15px;
    position: relative;

    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 6px;
      height: 6px;
      margin-top: 8px;
      border-radius: 50%;
      box-sizing: border-box;
      border: 1px solid $van-doc-dark-grey;
    }
  }

  hr {
    border: 0 none;
    border-top: 1px solid #eee;
  }

  p > code,
  li > code,
  table code {
    margin: 2px 3px;
    padding: 2px 5px;
    display: inline;
    box-shadow: none;
    background-color: #f0f2f5;
  }

  section {
    padding: 30px;
    overflow: hidden;
  }

  blockquote {
    padding: 16px;
    margin: 20px 0 0;
    font-size: 14px;
    border-radius: 4px;
    background-color: #ecf9ff;
    color: rgba(52, 73, 94, .8);
    border-left: 5px solid #50bfff;
  }

  img {
    margin: 12px 0;
  }

  &--changelog {
    strong {
      display: block;
      margin: 12px 0;
      font-size: 15px;
      font-weight: 500;
    }

    h3 {
      font-size: 20px;

      + p code {
        margin: 0;
      }

      a {
        color: inherit;
      }
    }
  }
}
</style>
