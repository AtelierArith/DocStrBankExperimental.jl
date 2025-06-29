```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                               ▄▞▀▀▀▀▀▄▖                              │ 
  │                             ▄▀        ▝▚▖                            │ 
  │                           ▗▞            ▝▄                           │ 
  │                          ▗▘               ▚                          │ 
  │                         ▞▘                 ▀▖                        │ 
  │                        ▞                    ▝▖                       │ 
  │                      ▗▞                      ▐▖                      │ 
  │                     ▗▘                        ▝▚                     │ 
  │                    ▄▘                           ▚▖                   │ 
  │                   ▞                              ▝▖                  │ 
  │                 ▗▀                                ▝▚                 │ 
  │               ▗▞▘                                   ▀▄               │ 
  │             ▗▞▘                                       ▀▄             │ 
  │          ▗▄▞▘                                           ▀▄▄          │ 
0 │ ▄▄▄▄▄▄▄▞▀▘                                                 ▀▀▄▄▄▄▄▄▄▖│ 
  └──────────────────────────────────────────────────────────────────────┘ 
  0                                                                     70


kaiser(n::Integer, α::Real; padding::Integer=0, zerophase::Bool=false)
kaiser(dims, α; padding=0, zerophase=false)
```

長さ `n` のカイザーウィンドウは `α` によってパラメータ化されます。カイザーウィンドウは、ベッセル関数に依存する簡略化された定義を使用して、DPSSウィンドウ（`dpss` によって与えられる）を近似します。`α` の値が大きいほど主ローブが広くなりますが、サイドローブは低くなります。通常、`α` は約 3 に設定されます。

ウィンドウは連続関数をサンプリングすることによって定義されます：

```
         ⎛  ⎛   _________⎞⎞
         ⎜  ⎜  ╱        2⎟⎟
w(x) = I₀⎝πα⎝╲╱ 1 - (2x) ⎠⎠
       ────────────────────
               I₀(πα)
```

範囲 `[-0.5, 0.5]` で。

ここで I₀(⋅) は第一種のゼロ次修正ベッセル関数です。

単一の `n` ではなく `dims` `Tuple` を提供すると、2D ウィンドウが構築されます。`α`、`padding`、および `zerophase` は、水平および垂直の両方に対して単一の値として、またはそれらを別々に指定するための 2-タプルとして与えることができます。

`zerophase` が `false`（デフォルト）である場合、ウィンドウはインデックス `(n+1)/2` の周りに中心が置かれ、これは FIR フィルタ設計に一般的に使用されます。これらは FIR フィルタ設計にしばしば使用され、通常は奇数長です。偶数長のウィンドウの場合、ウィンドウの中心がサンプルの間に位置することに注意してください。

`zerophase` が `true` の場合、ウィンドウはインデックス 1 の周りに中心が置かれ（負の半分がベクトルの末尾にラップされます）、さらにこれにより「周期的」ウィンドウが作成されます。これは、パディングがない場合、ウィンドウの左端と右端が同じサンプルにラップされることを意味し、ウィンドウの長さは `n+1` 長の非 `zerophase` ウィンドウと同じになります。あるいは、連続の `zerophase` ウィンドウが幅 `n` であり、非 `zerophase` ウィンドウが長さ `n-1` であると考えることができます。`zerophase` ウィンドウは FFT 処理でしばしば使用され、通常は偶数長です。
