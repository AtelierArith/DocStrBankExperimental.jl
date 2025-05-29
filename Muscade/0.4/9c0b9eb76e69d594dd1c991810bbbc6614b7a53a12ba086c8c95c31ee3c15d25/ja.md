```
dofres = getdof(state;[class=:X],field=:somefield,nodID=[nodids...],[orders=[0]])
```

同じクラスとフィールドのdofの値を、さまざまなノードとさまざまな状態で取得します。

`state`がベクトルの場合、出力`dofres`のサイズは`(ndof,nder+1,nstate)`です。`state`がスカラーの場合、出力`dofres`のサイズは`(ndof,nder+1)`です。

参照: [`getresult`](@ref), [`addnode!`](@ref), [`solve`](@ref)
