```julia
commnt(; ...)
commnt(kernelfile; ...)
commnt(
    kernelfile,
    commentfile;
    add,
    extract,
    read,
    delete,
    help,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

COMMNTは、SPICEバイナリカーネルファイルからコメントを読み取り、追加し、抽出し、または削除するコマンドラインプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数        | 同等のもの | 説明                  |
|:--------- |:----- |:------------------- |
| `add`     | `-a`  | バイナリカーネルにコメントを追加する  |
| `extract` | `-e`  | バイナリカーネルからコメントを抽出する |
| `read`    | `-r`  | バイナリカーネル内のコメントを読み取る |
| `delete`  | `-d`  | バイナリカーネルからコメントを削除する |
| `help`    | `-h`  | ヘルプメッセージを表示する       |
