```
KKTVectorFieldNormSq{O<:ConstrainedManifoldObjective}
```

KKT条件のベクトル場 $F$ のノルムの二乗を実装します。これは不等式制約のためのスラック変数を含みます。詳細は [`KKTVectorField`](@ref) を参照してください。このファンクタはノルムを適用します。[LaiYoshise:2024](@cite) では、これはメリット関数と呼ばれています。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

# コンストラクタ

```
KKTVectorFieldNormSq(cmo::ConstrainedManifoldObjective)
```

# 例

いくつかの [`ConstrainedManifoldObjective`](@ref) `cmo` に対して `f = KKTVectorFieldNormSq(cmo)` を定義し、$N$ を $\mathcal M×ℝ^m×ℝ^n×ℝ^m$ の積多様体とします。次に、`f(N, q)` と呼び出すことができ、ここで `q` は `N` 上の点です。
