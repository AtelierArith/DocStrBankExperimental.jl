```
on(f, observable::AbstractObservable; weak = false)
```

関数 `f` を `observable` のリスナーとして追加します。`observable` の値が `observable[] = val` を介して設定されるたびに、`f` が `val` で呼び出されます。

`f` と `observable` をラップする [`ObserverFunction`](@ref) を返し、`off(f, observable)` の代わりに `off(observerfunction)` を呼び出すことで簡単に切断できるようにします。代わりに古い `Observable` から新しい `Observable` を計算したい場合は、[`map(f, ::Observable)`](@ref) を使用してください。

`weak = true` が設定されている場合、返された `ObserverFunction` がどこにも参照されなくなり、ガーベジコレクトされると新しい接続は削除されます。これは、親オブジェクトが外部のオブザーバブルに接続し、結果として得られた `ObserverFunction` インスタンスを保存する場合に便利です。その後、その親オブジェクトがガーベジコレクトされると、弱いオブザーバブル接続は自動的に削除されます。

# 例

```jldoctest; setup=:(using Observables)
julia> obs = Observable(0)
Observable{Int64} with 0 listeners. Value:
0

julia> on(obs) do val
           println("current value is ", val)
       end
(::Observables.ObserverFunction) (generic function with 0 methods)

julia> obs[] = 5;
current value is 5
```
