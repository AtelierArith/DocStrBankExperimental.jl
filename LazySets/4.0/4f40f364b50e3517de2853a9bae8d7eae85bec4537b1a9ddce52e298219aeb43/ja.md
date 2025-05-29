```
reduce_order(Z::AbstractZonotope, r::Real,
             [method]::AbstractReductionMethod=GIR05())
```

ゾノトピック集合の次数を、より少ない生成子を持つゾノトープで過大評価することによって減少させます。

### 入力

  * `Z`      – ゾノトピック集合
  * `r`      – 希望する次数
  * `method` – （オプション、デフォルト: `GIR05()`）使用される削減方法

### 出力

可能であれば、より少ない生成子を持つ新しいゾノトープ。

### アルゴリズム

利用可能なアルゴリズムは次のとおりです：

```jldoctest; setup = :(using LazySets: subtypes, AbstractReductionMethod)
julia> subtypes(AbstractReductionMethod)
3-element Vector{Any}:
 LazySets.ASB10
 LazySets.COMB03
 LazySets.GIR05
```

各アルゴリズムの文献については、ドキュメントを参照してください。これらの方法は、与えられたゾノトピック集合 `Z` を、最も「代表的な」生成子を含むゾノトープ `K` と、ボックスの過大評価を使用して削減された生成子 `L` を含むゾノトープ `L` に分割します。私たちは [YangS18](@citet) からの表記法に従います。また、[KopetzkiSA17](@citet) も参照してください。
