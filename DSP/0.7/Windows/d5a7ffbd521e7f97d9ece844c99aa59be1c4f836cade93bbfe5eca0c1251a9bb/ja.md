```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                                ▄▞▀▀▀▄▖                               │ 
  │                            ▗▄▞▀      ▝▀▄▖                            │ 
  │                         ▗▄▀▘            ▝▀▄▖                         │ 
  │                      ▗▄▀▘                  ▝▀▄▖                      │ 
  │                   ▗▄▀▘                        ▝▀▄▖                   │ 
  │                ▗▄▀▘                              ▝▀▄▄                │ 
  │             ▗▄▀▘                                     ▀▚▄             │ 
  │          ▗▄▀▘                                           ▀▙▄          │ 
  │       ▄▄▀▘                                                 ▀▚▄       │ 
  │    ▄▞▀                                                        ▀▚▄    │ 
  │ ▄▞▀                                                              ▀▚▄ │ 
  │▀                                                                    ▀│ 
  │                                                                      │ 
  │                                                                      │ 
0 │                                                                      │ 
  └──────────────────────────────────────────────────────────────────────┘ 
  1                                                                      7


triang(n::Integer; padding::Integer=0, zerophase::Bool=false)
triang(dims; padding=0, zerophase=false)
```

長さ `n` の三角窓を `padding` ゼロで作成します。三角窓は端点でゼロには達しません。奇数の `n` の場合、`triang` 窓は `n+2` 点の [`bartlett`](@ref) 窓の中心の `n` 点です（つまり、窓の外側のサンプルはゼロになります）。偶数の `n` の場合、窓の傾きは `n-1` 窓と同じですが、半サンプル遅延されるため、ゼロ点は窓の端から 1/2 サンプル先になります。

窓は連続関数をサンプリングすることによって定義されます：

```
        ⎛    2(n-1)
        ⎜1 - ────── abs(x)     n は偶数
        ⎜       n
w(x) =  ⎜
        ⎜    2(n-1)
        ⎜1 - ────── abs(x)     n は奇数
        ⎝     n+1
```

範囲 `[-0.5, 0.5]` で。

単一の `n` の代わりに `dims` `Tuple` を提供すると、2D 窓が構築されます。`padding` と `zerophase` は、水平と垂直の両方に対して単一の値として、またはそれらを別々に指定するための 2-タプルとして与えることができます。

`zerophase` が `false` の場合（デフォルト）、窓はインデックス `(n+1)/2` の周りに中心が置かれ、これは FIR フィルタ設計で一般的に使用されます。これらは FIR フィルタ設計にしばしば使用され、通常は奇数長です。偶数長の窓の場合、窓の中心がサンプルの間に位置することに注意してください。

`zerophase` が `true` の場合、窓はインデックス 1 の周りに中心が置かれ（負の半分がベクトルの端にラップされます）、さらにこれにより「周期的」窓が作成されます。これは、パディングがない場合、窓の左端と右端が同じサンプルにラップされることを意味し、窓の長さは `n+1` 長の非 `zerophase` 窓と同じになります。あるいは、連続の `zerophase` 窓が幅 `n` で、非 `zerophase` 窓が長さ `n-1` であると考えることができます。`zerophase` 窓は FFT 処理でしばしば使用され、通常は偶数長です。

`zerophase` が `true` の場合、上記の窓の式で `n` の代わりに `n+1` を代入します。
