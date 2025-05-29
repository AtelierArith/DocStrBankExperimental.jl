```
ilast = findlastassigned(state)
```

ベクトル `state` において、最初の非割り当て要素の前の要素のインデックス `ilast` を見つけます。

マルチステップ分析では、`solve` はユーザーが要求したステップ数と同じ長さのベクトル `state` を返します。分析が中止された場合、`solve` はそれでも `state` の最初の部分に利用可能な結果を返し、ベクトル `state[1:ilast]` は完全に割り当てられています。

参照: [`solve`](@ref)
