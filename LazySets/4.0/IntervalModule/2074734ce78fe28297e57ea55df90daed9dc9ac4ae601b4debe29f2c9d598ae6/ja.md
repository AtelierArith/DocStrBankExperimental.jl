```
Interval{N} <: AbstractHyperrectangle{N}
```

実数直線上の区間を表す型です。数学的には、次の形をしています。

$$
[a, b] := \{ a ≤ x ≤ b \} ⊆ ℝ.
$$

### フィールド

  * `dat` – 指定された区間のデータコンテナ

### 注意事項

この型は、区間の表現と算術演算のために [IntervalArithmetic.jl](https://juliaintervals.github.io/IntervalArithmetic.jl/stable/) ライブラリに依存しています。

### 例

一次元の区間は、実閉区間の象徴的な表現です。

異なる方法で区間を作成できます。最も簡単な方法は、数のペアを渡すことです：

```jldoctest interval_constructor
julia> x = Interval(0.0, 1.0)
Interval{Float64}([0, 1])
```

2ベクトルも可能です：

```jldoctest interval_constructor
julia> x = Interval([0.0, 1.0])
Interval{Float64}([0, 1])
```

`IntervalArithmetic.Interval` からも区間を構築できます。現在のスコープで `IntervalArithmetic` パッケージが読み込まれている場合、名前の衝突があるため、`Interval` の前にパッケージ名を付ける必要があります。

```jldoctest interval_constructor
julia> using IntervalArithmetic
WARNING: using IntervalArithmetic.Interval in module Main conflicts with an existing identifier.

julia> x = LazySets.Interval(IntervalArithmetic.Interval(0.0, 1.0))
Interval{Float64}([0, 1])

julia> dim(x)
1

julia> center(x)
1-element Vector{Float64}:
 0.5
```

通常のペアワイズ算術演算子 `-` と `*` は、区間算術で知られている標準的な方法で解釈されるため、結果は `Interval` になります。なお、`+` はこのライブラリでは一般的に遅延ミンコフスキー和に使用されます。

他の数値型の区間も作成できます。例えば、有理数区間：

```jldoctest interval_constructor
julia> Interval(0//1, 2//1)
Interval{Rational{Int64}}([0//1, 2//1])
```
