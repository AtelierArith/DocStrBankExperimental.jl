@localize args... expr

書くことは

```
@localize x y z expr
```

は書くことと同等です

```
let x=x, y=y, z=z
    expr
end
```

これは、クロージャを使用する際にキャプチャされた変数のボクシングを回避するのに役立ちます。

ボックス化された変数に関する詳細情報は、https://juliafolds2.github.io/OhMyThreads.jl/stable/literate/boxing/boxing/ を参照してください。
