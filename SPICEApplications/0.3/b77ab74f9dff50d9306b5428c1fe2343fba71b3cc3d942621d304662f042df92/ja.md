```julia
mkdsk(
;
    setup,
    input,
    output,
    help,
    template,
    usage,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MKDSKは、拡張オブジェクトの形状データを含むテキストファイルからSPICEデジタルシェイプカーネル（DSK）ファイルを作成するユーティリティプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数         | 同等のもの                   | 説明           |
|:---------- |:----------------------- |:------------ |
| `setup`    | `-setup <セットアップファイル名>`  | セットアップファイル名  |
| `input`    | `-input <入力形状データファイル名>` | 入力形状データファイル名 |
| `output`   | `-output <出力DSKファイル名>`  | 出力DSKファイル名   |
| `help`     | `-h│-help`              | ヘルプを表示       |
| `template` | `-t│-template`          | テンプレートを表示    |
| `usage`    | `-u│-usage`             | 使用法を表示       |
| `version`  | `-v│-version`           | バージョンを表示     |
