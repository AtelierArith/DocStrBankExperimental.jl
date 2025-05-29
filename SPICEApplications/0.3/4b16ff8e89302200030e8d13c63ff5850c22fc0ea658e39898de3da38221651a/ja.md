```julia
dskexp(
;
    dsk,
    text,
    format,
    precision,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

DSKEXPは、DSKファイルからテキストファイルにデータをエクスポートするコマンドラインプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数          | 同等のもの                         | 説明                |
|:----------- |:----------------------------- |:----------------- |
| `dsk`       | `-dsk <dsk>`                  | DSKカーネル           |
| `text`      | `-text <出力名>`                 | 出力名               |
| `format`    | `-format <MKDSKフォーマットコード/名前>` | MKSDKフォーマットコード/名前 |
| `precision` | `-prec <頂点仮数桁数 (1:17)>`       | 頂点仮数桁数            |
