```
birkhoff_extrapolation(h::Function, F::Function, x0::AbstractVector,
                       N::Integer, K::Integer; iterative::Bool=false,
                       x_prev::Union{AbstractArray,Nothing}=nothing,
                       rre::Bool=false)
```

入力として、初期点 `x0`、シンプレクティック写像 `F`、および観測可能量 `h`（デフォルトの `h = (x)->x` を選択可能）を取ります。次に、メソッドは

1. 時系列 xs[:,n+1] = Fⁿ(x0) を計算します。
2. 観測可能量の系列 hs[:,n] = h(xs[:,n]) を計算します。
3. hs に対して系列外挿（RRE または MPE）を行い、長さ `2K+1` のモデル `c`（`K` 個の未知数を持つ）を取得し、各ウィンドウに適用される外挿値と残差を得ます。
4. `c, sums, resid, xs, hs[, history]` として返します。ここで `history` は、`iterative=true` の場合にのみ返される反復ソルバーからの診断情報です。

シーケンスの一部をすでに知っている場合は `x_prev` を使用しますが、全体は知らない場合に使用します。
