```julia
mkspk(
;
    setup,
    input,
    output,
    add,
    usage,
    help,
    template,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MKSPKは、軌道情報を含むテキストファイルからSPKファイルを作成するプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数         | 同等のもの                   | 説明                  |
|:---------- |:----------------------- |:------------------- |
| `setup`    | `-setup <セットアップファイル名>`  | セットアップファイル名         |
| `input`    | `-input <入力形状データファイル名>` | 入力形状データファイル名        |
| `output`   | `-output <出力DSKファイル名>`  | 出力DSKファイル名          |
| `add`      | `-append`               | 追加; 出力ファイルは新しい必要がある |
| `help`     | `-h│-help`              | ヘルプを表示              |
| `template` | `-t│-template`          | テンプレートを表示           |
| `usage`    | `-u│-usage`             | 使用法を表示              |
