```
NLevelSpace <: HilbertSpace
NLevelSpace(name::Symbol,levels,GS=levels[1])
```

`N` 個の離散エネルギーレベルからなるオブジェクトのための [`HilbertSpace`](@ref) を定義します。与えられた `levels` は、レベルの数を指定する整数またはレベルの反復可能なコレクションでなければなりません。引数 `GS` は、基底状態として扱うべき状態を指定し、簡約中に人口保存を使用して書き換えられます。詳細については、[`Transition`](@ref) を参照してください。

# 例:

```
julia> ha = NLevelSpace(:a,3)
ℋ(a)

julia> ha = NLevelSpace(:a,(:g,:e))
ℋ(a)
```
