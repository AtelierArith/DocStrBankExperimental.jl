`struct SphericalHarmonics` : 実数球面調和関数基底を表すデータ型。

### 基底オブジェクトを生成するコンストラクタ

```julia
basis = SphericalHarmonics(L::Integer; kwargs...)
```

### キーワード引数:

  * `normalisation = :L2` : 基底の正規化を選択します。デフォルトは単位球面上で直交正規化を行うことです。
  * `static = (L<=15)` : 出力が `SVector` である生成されたコードを使用するかどうかを決定しますが、コンパイラとスタックのフットプリントが大きくなります。
  * `T = Float64` : 基底パラメータが格納されるデータ型。出力型は実行時に推論されますが、一般的なルールは `FloatX` 出力には `T = FloatX` を使用することです。

### 使用例:

```julia
using StaticArrays, SpheriCart
basis = SphericalHarmonics(4)
# 単一入力で基底を評価
𝐫 = @SVector randn(3)
Z = basis(𝐫)
Z = compute(basis, 𝐫)
# 複数入力（バッチ処理）で基底を評価
R = [ @SVector randn(3) for _ = 1:32 ]
Z = basis(Rs)
Z = compute(basis, Rs)

# 実装予定:
# Z, ∇Z = compute_and_gradients(basis, 𝐫)
# Z, ∇Z, ∇²Z = compute_and_hessian(basis, 𝐫)
```

詳細についてはドキュメントを参照してください。
