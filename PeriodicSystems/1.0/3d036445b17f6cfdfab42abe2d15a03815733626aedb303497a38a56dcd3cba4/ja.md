```
 isstable(psys[, K = 1]; smarg = 1, fast = false, offset = sqrt(ϵ), kwargs...) -> Bool
```

連続時間周期システム `psys` が安定な特性乗数のみを持つ場合は `true` を返し、それ以外の場合は `false` を返します。

安定性を評価するためには、特性乗数（すなわち、モノドロミー行列の固有値）の絶対値が `smarg-β` より小さい必要があります。ここで、`smarg` は離散時間の安定性マージン（デフォルト: `smarg = 1`）であり、`β` は固有値の安定性を数値的に評価するために使用されるキーワードパラメータ `offset = β` で指定されます。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業用の機械精度です。

モノドロミー行列は、周期係数を持つ同次線形ODEを数値的に統合することによって計算された `K` 状態遷移行列の積として決定されます（デフォルト: `K = 1`）。`fast = false`（デフォルト）の場合、特性乗数は周期的シュール分解に基づくアプローチを使用して計算されます[1]。一方、`fast = true` の場合は、適切なリフトされたペンシルの構造を利用した削減[2]が使用されます。この後者のオプションは、大量の行列に対して不正確な結果をもたらすことがあります。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
