```
state = setdof!(state,value        ;[class=:X],field=:somefield,                  [order=0])
state = setdof!(state,value::Vector;[class=:X],field=:somefield,nodID=[nodids...],[order=0])
```

同じクラスとフィールドのdofの値を、さまざまなノードとさまざまな状態で設定します。方法は2つあります：

1. 単一の`value`がモデル内のすべての関連ノードに適用されます。
2. `value`と`nodID`は同じ長さのベクトルであり、`value`の各要素が対応するノードに適用されます。

`setdof!`は、入力の`state`変数を変更する点で特異ですが、関数として使用する必要があります。`stateout = setdof!(statein,value;class=:X,field=:somefield,order=1)`のような呼び出しは2つの方法で結果が得られます：もし`state`がすでに1次の`X`の導関数を格納している場合、`statein`は変更され、`statein===stateout`となります。そうでなければ、`statein`は変更されず、`stateout`は新しいオブジェクトで、`statein`とできるだけ多くのメモリを共有します。混乱を避けるために、常に上記の構文を使用してください。

参照：[`getresult`](@ref), [`addnode!`](@ref), [`solve`](@ref)
