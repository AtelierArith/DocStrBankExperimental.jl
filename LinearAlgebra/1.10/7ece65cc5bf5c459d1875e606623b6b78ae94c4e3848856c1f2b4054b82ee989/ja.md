```
svd(A, B) -> GeneralizedSVD
```

`A`と`B`の一般化SVDを計算し、`[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`となる`GeneralizedSVD`因子化オブジェクト`F`を返します。

  * `U`はM-by-Mの直交行列です。
  * `V`はP-by-Pの直交行列です。
  * `Q`はN-by-Nの直交行列です。
  * `D1`は最初のKエントリに1があるM-by-(K+L)の対角行列です。
  * `D2`は右上のL-by-Lブロックが対角行列であるP-by-(K+L)の行列です。
  * `R0`は右端の(K+L)-by-(K+L)ブロックが非特異上三角行列である(K+L)-by-Nの行列です。

`K+L`は行列`[A; B]`の有効な数値ランクです。

分解を繰り返すことで、成分`U`、`V`、`Q`、`D1`、`D2`、および`R0`が得られます。

一般化SVDは、`A`にどれだけ属するかと`B`にどれだけ属するかを比較したい場合、例えばヒトと酵母のゲノム、信号とノイズ、またはクラスタ間とクラスタ内の比較などのアプリケーションで使用されます。（議論についてはEdelmanとWangを参照してください: https://arxiv.org/abs/1901.00485）

これは`[A; B]`を`[UC; VS]H`に分解し、`[UC; VS]`は`[A; B]`の列空間の自然な直交基底であり、`H = RQ'`は`[A;B]`の行空間の自然な非直交基底です。上部の行は`A`行列に最も密接に帰属し、下部は`B`行列に帰属します。多重コサイン/サイン行列`C`と`S`は、`A`と`B`のどれだけの割合を測定するかの多重測定を提供し、`U`と`V`はこれらが測定される方向を提供します。

# 例

```jldoctest
julia> A = randn(3,2); B=randn(4,2);

julia> F = svd(A, B);

julia> U,V,Q,C,S,R = F;

julia> H = R*Q';

julia> [A; B] ≈ [U*C; V*S]*H
true

julia> [A; B] ≈ [F.U*F.D1; F.V*F.D2]*F.R0*F.Q'
true

julia> Uonly, = svd(A,B);

julia> U == Uonly
true
```
