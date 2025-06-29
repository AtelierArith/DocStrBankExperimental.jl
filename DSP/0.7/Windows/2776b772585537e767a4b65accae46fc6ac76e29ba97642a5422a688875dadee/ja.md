```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                                 ▄▀▀▚▖                                │ 
  │                              ▗▄▀    ▝▚▄                              │ 
  │                            ▗▞▘         ▀▄                            │ 
  │                          ▄▞▘             ▀▄▖                         │ 
  │                        ▄▀                  ▝▚▖                       │ 
  │                     ▗▄▀                      ▝▄▄                     │ 
  │                   ▗▞▘                           ▀▄                   │ 
  │                 ▄▞▘                               ▀▄▖                │ 
  │               ▄▀                                    ▝▚▖              │ 
  │            ▗▞▀                                        ▝▀▄            │ 
  │          ▗▞▘                                             ▀▄          │ 
  │        ▄▀▘                                                 ▀▚▖       │ 
  │      ▄▀                                                      ▝▚▖     │ 
  │   ▗▞▀                                                          ▝▀▄   │ 
0 │ ▄▞▘                                                               ▀▄▖│ 
  └──────────────────────────────────────────────────────────────────────┘ 
  0                                                                     70


bartlett(n::Integer; padding::Integer=0, zerophase::Bool=false)
bartlett(dims; padding=0, zerophase=false)
```

長さ `n` のバートレットウィンドウ。バートレットウィンドウは、端点で0に達する三角形のウィンドウです。これは、長さ `(n-1)/2` の2つの矩形ウィンドウを畳み込み、ゼロの端点を追加することに相当します。端点でゼロに達しないウィンドウについては `triang` を参照してください。

ウィンドウは、連続関数をサンプリングすることによって定義されます：

```
1 - abs(2x)
```

範囲 `[-0.5, 0.5]` で

単一の `n` の代わりに `dims` の `Tuple` を提供すると、2Dウィンドウが構築されます。`padding` と `zerophase` は、水平と垂直の両方に対して単一の値として、またはそれらを別々に指定するための2タプルとして与えることができます。

`zerophase` が `false` （デフォルト）である場合、ウィンドウはインデックス `(n+1)/2` の周りに中心が置かれ、これは一般的にFIRフィルタ設計に使用されます。これらはFIRフィルタ設計にしばしば使用され、通常は奇数長です。偶数長のウィンドウの場合、ウィンドウの中心がサンプルの間に位置することに注意してください。

`zerophase` が `true` の場合、ウィンドウはインデックス1の周りに中心が置かれ（負の半分がベクトルの末尾にラップされます）、さらにこれにより「周期的」ウィンドウが作成されます。これは、パディングがない場合、ウィンドウの左端と右端が同じサンプルにラップされることを意味します。したがって、ウィンドウの長さは `n+1` 長の非 `zerophase` ウィンドウと同じになります。あるいは、連続の `zerophase` ウィンドウが幅 `n` であり、非 `zerophase` ウィンドウが長さ `n-1` であると考えることができます。`zerophase` ウィンドウはFFT処理でしばしば使用され、通常は偶数長です。
