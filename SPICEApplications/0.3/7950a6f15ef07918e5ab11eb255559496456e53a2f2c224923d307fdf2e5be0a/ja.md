```julia
frmdiff(
;
    kernels,
    from1,
    to1,
    frame1,
    supporting_kernels1,
    from2,
    to2,
    frame2,
    supporting_kernels2,
    angular,
    angularframe,
    start,
    stop,
    numpoints,
    timestep,
    timeformat,
    report,
    rotation,
    units,
    sigdigs,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

FRMDIFFは、SPICEに知られている参照フレームの向きをサンプリングするプログラムであるか、SPICEに知られている2つの参照フレームの向きの違いを計算し、この向きまたはこれらの違いを表示するか、またはそれに関する統計を表示します。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数                    | 同等のもの                                                                     | 説明                              |
|:--------------------- |:------------------------------------------------------------------------- |:------------------------------- |
| `kernels`             | `-k  <supporting kernel(s) name(s)>`                                      | supporting kernel(s) name(s)>   |
| `from1`               | `-f1 <first``from'' frame, name or ID>`                                   | 最初の "from" フレーム、名前またはID         |
| `to1`                 | `-t1 <first``to'' frame, name or ID>`                                     | 最初の "to" フレーム、名前またはID           |
| `frame1`              | `-c1 <first frame for coverage look up, name or ID>`                      | カバレッジルックアップのための最初のフレーム、名前またはID  |
| `supporting_kernels1` | `-k1 <additional supporting kernel(s) for first file>`                    | 最初のファイルのための追加のサポートカーネル          |
| `from2`               | `-f2 <second``from'' frame, name or ID>`                                  | 2番目の "from" フレーム、名前またはID        |
| `to2`                 | `-t2 <second``to'' frame, name or ID>`                                    | 2番目の "to" フレーム、名前またはID          |
| `frame2`              | `-c2 <second frame for coverage look up, name or ID>`                     | カバレッジルックアップのための2番目のフレーム、名前またはID |
| `supporting_kernels2` | `-k2 <additional supporting kernel(s) for second file>`                   | 2番目のファイルのための追加のサポートカーネル         |
| `angular`             | `-a  <compare angular velocities: yes│no (default: no)>`                  | 角速度を比較する                        |
| `angularframe`        | `-m  <frame for angular velocities: from│to (default: from)>`             | 角速度のためのフレーム                     |
| `start`               | `-b  <interval start time>`                                               | インターバルの開始時間                     |
| `stop`                | `-e  <interval stop time>`                                                | インターバルの終了時間                     |
| `numpoints`           | `-n  <number of points: 1 to 1000000 (default: 1000)>`                    | ポイントの数                          |
| `timestep`            | `-s  <time step in seconds>`                                              | 秒単位の時間ステップ                      |
| `timeformat`          | `-f  <time format: et│sclk│sclkd│ticks│picture_for_TIMOUT (default: et)>` | 時間フォーマット                        |
| `report`              | `-t  <report: basic│stats│dumpaa│dumpm│dumpqs│dumpqo│dumpea│dumpc│dumpg>` | レポート                            |
| `rotation`            | `-o  <rotation axes order (default: z y x)>`                              | 回転軸の順序                          |
| `units`               | `-x  <units for output angles> (only for -t dumpaa and -t dumpea)`        | 出力角度の単位                         |
| `sigdigs`             | `-d  <number of significant digits: 6 to 17 (default: 14)>`               | 有効数字の数                          |
