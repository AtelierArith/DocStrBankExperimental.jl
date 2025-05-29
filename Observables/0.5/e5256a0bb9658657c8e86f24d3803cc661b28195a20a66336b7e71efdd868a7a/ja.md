```
obs = map(f, arg1::AbstractObservable, args...; ignore_equal_values=false)
```

新しい observable `obs` を作成します。これは `arg1` と `args` から抽出された値に適用された `f` の結果を含みます（すなわち、`f(arg1[], ...)`）。`arg1` はディスパッチの理由から observable でなければなりません。`args` には任意の数の `Observable` オブジェクトを含めることができます。`f` には、各引数として observables に含まれる値が渡されます。`args` の他のオブジェクトはそのまま渡されます。

`obs` の値が必要ない場合、引数が更新されるたびに `f` を実行したいだけであれば、代わりに [`on`](@ref) または [`onany`](@ref) を使用してください。

# 例

```jldoctest; setup=:(using Observables)
julia> obs = Observable([1,2,3]);

julia> map(length, obs)
Observable(3)
```
