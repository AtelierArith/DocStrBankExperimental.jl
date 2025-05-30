```
gsa(f, method::GSAMethod, param_range; samples, batch=false)
```

ここで：

  * `y=f(x)` は、単一のベクトルを受け取り、単一のベクトルまたはスカラーを出力する関数です。`batch=true` の場合、`f` は行ごとにパラメータのセットを持つ行列を受け取り、各行のパラメータに対応する出力を持つ行列を返します。
  * `method` は利用可能な GSA メソッドの1つです。
  * `param_range` は、与えられたパラメータ `i` の上限と下限のタプルのベクトルです。
  * `samples` は設計行列のパラメータのサンプル数のための必須キーワード引数です。これは、[Fractional Factorial Method](@ref) および [Morris Method](@ref) には関連しないことに注意してください。

さらに、

[Delta Moment-Independent Method](@ref)、[EASI Method](@ref)、および [Regression Method](@ref) では、次のように入力および出力の行列ベースのメソッドが利用可能です：

```julia
res = gsa(X, Y, method)
```

ここで：

  * `X` はパラメータ * サンプルの行列で、パラメータ値を持っています。
  * `Y` は出力次元 * サンプル数の行列で、`X` の列で評価されます。
  * `method` は以下の GSA メソッドの1つです。

[Sobol Method](@ref) では、前述のパラメータ範囲ベースのメソッドの代わりに、次の設計行列ベースのメソッドを使用できます：

```julia
effects = gsa(f, method, A, B; batch=false)
```

ここで `A` と `B` は設計行列で、各行がパラメータのセットです。設計行列を生成するために、[QuasiMonteCarlo.jl](https://docs.sciml.ai/QuasiMonteCarlo/stable/) の `generate_design_matrices` を使用できることに注意してください。
