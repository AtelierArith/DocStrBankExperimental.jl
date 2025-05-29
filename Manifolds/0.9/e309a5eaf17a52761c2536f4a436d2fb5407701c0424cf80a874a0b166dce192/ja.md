```
Euclidean{T,𝔽} <: AbstractManifold{𝔽}
```

ユークリッドベクトル空間。

# コンストラクタ

```
Euclidean(n)
```

$$
n
$$

次元ベクトル空間$ℝ^n$を生成します。

```
Euclidean(n₁,n₂,...,nᵢ; field=ℝ, parameter::Symbol = :field)
𝔽^(n₁,n₂,...,nᵢ) = Euclidean(n₁,n₂,...,nᵢ; field=𝔽)
```

$$
k = n_1 ⋅ n_2 ⋅ … ⋅ n_i
$$

の値のベクトル空間、すなわち多様体$𝔽^{n_1, n_2, …, n_i}$を生成します。ここで、$𝔽\in\{ℝ,ℂ\}$であり、その要素は$n_1 × n_2 × … × n_i$の配列として解釈されます。$i=2$の場合、行列空間が得られます。デフォルトの`field=ℝ`は`field=ℂ`に設定することもできます。この空間の次元は$k \dim_ℝ 𝔽$であり、ここで$\dim_ℝ 𝔽$は[`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`)で、フィールド$𝔽$の次元です。

`parameter`: 型パラメータを使用して`n`を格納するかどうか。デフォルトではサイズは型に格納されます。値は`:field`または`:type`のいずれかです。

```
Euclidean(; field=ℝ)
```

`ℝ`-または`ℂ`-値の実数または複素数の不変値のための1次元ユークリッド多様体を生成します（上記のコンストラクタからの1要素配列とは対照的です）。
