```
on(f, observable::AbstractObservable; weak = false, priority=0, update=false)::ObserverFunction
```

関数 `f` を `observable` のリスナーとして追加します。`observable` の値が `observable[] = val` を介して設定されるたびに、`f` が `val` で呼び出されます。

`f` と `observable` をラップし、`off(f, observable)` の代わりに `off(observerfunction)` を呼び出すことで簡単に切断できる [`ObserverFunction`](@ref) を返します。代わりに古い `Observable` から新しい `Observable` を計算したい場合は、[`map(f, ::Observable)`](@ref) を使用してください。

`weak = true` が設定されている場合、新しい接続は返された `ObserverFunction` がどこにも参照されなくなり、ガーベジコレクトされるとすぐに削除されます。これは、親オブジェクトが外部のオブザーバブルに接続し、結果として得られた `ObserverFunction` インスタンスを保存する場合に便利です。その後、その親オブジェクトがガーベジコレクトされると、弱いオブザーバブル接続が自動的に削除されます。

# 例

```julia
julia> obs = Observable(0)
Observable(0)

julia> on(obs) do val
           println("current value is ", val)
       end
ObserverFunction defined at REPL[17]:2 operating on Observable(0)
julia> obs[] = 5;
current value is 5
```

コールバックに優先度を与えることもでき、登録の順序に関係なく特定のコールバックを常に他のコールバックの前後で呼び出すことができます。最も高い優先度のコールバックが最初に呼び出され、デフォルトはゼロで、Int の全範囲を使用できます。したがって、次のようにできます。

```julia
julia> obs = Observable(0)
julia> on(obs; priority=-1) do x
           println("Hi from first added")
       end
julia> on(obs) do x
           println("Hi from second added")
       end
julia> obs[] = 2
Hi from second added
Hi from first added
```

`update=true` を設定すると、`on` はすぐに `f(obs[])` を呼び出します：

```julia
julia> on(Observable(1); update=true) do x
    println("hi")
end
hi
```
