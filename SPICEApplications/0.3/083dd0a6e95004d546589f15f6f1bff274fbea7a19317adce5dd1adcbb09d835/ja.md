```julia
spkdiff(
;
    kernels,
    body1,
    center1,
    frame1,
    supporting_kernels1,
    body2,
    center2,
    frame2,
    supporting_kernels2,
    start,
    stop,
    timestep,
    numstates,
    timeformat,
    sigdigs,
    report,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

SPKDIFFは、2つの天体の軌道を比較する手段や、SPICEカーネルのデータを使用して単一の天体の軌道をサンプリングする手段を提供します。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数                    | 同等のもの                                                                    | 説明                                                                     |
|:--------------------- |:------------------------------------------------------------------------ |:---------------------------------------------------------------------- |
| `kernels`             | `-k  <サポートカーネル名>`                                                        | -k  <サポートカーネル名>                                                        |
| `body1`               | `-b1 <最初の天体名またはID>`                                                      | -b1 <最初の天体名またはID>                                                      |
| `center1`             | `-c1 <最初の中心名またはID>`                                                      | -c1 <最初の中心名またはID>                                                      |
| `frame1`              | `-r1 <最初の参照フレーム名>`                                                       | -r1 <最初の参照フレーム名>                                                       |
| `supporting_kernels1` | `-k1 <最初のSPKのための追加サポートカーネル>`                                             | -k1 <最初のSPKのための追加サポートカーネル>                                             |
| `body2`               | `-b2 <2番目の天体名またはID>`                                                     | -b2 <2番目の天体名またはID>                                                     |
| `center2`             | `-c2 <2番目の中心名またはID>`                                                     | -c2 <2番目の中心名またはID>                                                     |
| `frame2`              | `-r2 <2番目の参照フレーム名>`                                                      | -r2 <2番目の参照フレーム名>                                                      |
| `supporting_kernels2` | `-k2 <2番目のSPKのための追加サポートカーネル>`                                            | -k2 <2番目のSPKのための追加サポートカーネル>                                            |
| `start`               | `-b  <間隔の開始時間>`                                                          | -b  <間隔の開始時間>                                                          |
| `stop`                | `-e  <間隔の終了時間>`                                                          | -e  <間隔の終了時間>                                                          |
| `timestep`            | `-s  <秒単位の時間ステップ>`                                                       | -s  <秒単位の時間ステップ>                                                       |
| `numstates`           | `-n  <状態の数: 2から1000000 (デフォルト: 1000)>`                                   | -n  <状態の数: 2から1000000 (デフォルト: 1000)>                                   |
| `timeformat`          | `-f  <出力時間形式 (デフォルト: J2000からのTDB秒)>`                                     | -f  <出力時間形式 (デフォルト: J2000からのTDB秒)>                                     |
| `sigdigs`             | `-d  <有効数字の数: 6から17 (デフォルト: 14)>`                                        | -d  <有効数字の数: 6から17 (デフォルト: 14)>                                        |
| `report`              | `-t  <レポートタイプ: basic│stats│dump│dumpvf│dumpc│dumpg (デフォルト: basic│dump)>` | -t  <レポートタイプ: basic│stats│dump│dumpvf│dumpc│dumpg (デフォルト: basic│dump)> |
