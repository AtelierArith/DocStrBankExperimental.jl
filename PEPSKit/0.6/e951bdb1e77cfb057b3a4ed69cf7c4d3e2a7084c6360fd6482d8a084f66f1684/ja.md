```julia
struct SVDAdjoint{F, R}
```

SVDアルゴリズム`fwd_alg`のラッパーで、定義された逆ルール`rrule_alg`を持ちます。`isnothing(rrule_alg)`の場合、Zygoteは自動的に前方呼び出しを微分します。

## フィールド

  * `fwd_alg::Any`
  * `rrule_alg::Any`

## コンストラクタ

```
SVDAdjoint(; kwargs...)
```

以下のキーワード引数に基づいて`SVDAdjoint`アルゴリズム構造体を構築します：

  * `fwd_alg::Union{Algorithm,NamedTuple}=(; alg::Symbol=sdd)`: 前方パスのSVDアルゴリズムで、`Algorithm`インスタンスまたは`alg`が以下のいずれかである`NamedTuple`として渡すことができます：

      * `:sdd` : LAPACKの`_gesdd`のTensorKitラッパー
      * `:svd` : LAPACKの`_gesvd`のTensorKitラッパー
      * `:iterative` : 指定された数の特異値とベクトルのみを計算する反復SVD、詳細は[`IterSVD`](@ref)を参照
  * `rrule_alg::Union{Algorithm,NamedTuple}=(; alg::Symbol=full)`: SVDの微分のための逆ルールアルゴリズム。`Algorithm`インスタンスを直接供給するか、`alg`が以下のいずれかである`NamedTuple`として供給できます：

      * `:full`: 線形問題を解決せず、代わりに完全なSVDへのアクセスを必要とするTensorKitの`tsvd`の逆ルールの修正バージョンを使用します。詳細は[`FullSVDReverseRule`](@ref)を参照。
      * `:gmres`: GMRES反復線形ソルバー、詳細は[KrylovKitのドキュメント](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.GMRES)を参照
      * `:bicgstab`: BiCGStab反復線形ソルバー、詳細は[KrylovKitのドキュメント](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.BiCGStab)を参照
      * `:arnoldi`: アーノルディクリロフアルゴリズム、詳細は[KrylovKitのドキュメント](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.Arnoldi)を参照
