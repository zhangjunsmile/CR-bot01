## CR-BOT01

### 使用方式

1. 在仓库的 Actions secrets 中添加 `OPENAI_API_KEY`

2. 在仓库的 .github/workflows 目录中添加 cr.yml 文件，内容如下

```
name: Code Review

permissions:
  contents: read
  pull-requests: write

on:
  pull_request:
    types: [opened, reopened, synchronize]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: zhangjunsmile/CR-bot01@main
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}

```
