```
@forcedef [function definition]
```

強制抽出のための関数デコレーター。

`forcedef` で装飾された関数定義は、2つのメソッドに展開されます。後者のメソッドには、値を蓄積するために使用できる追加の最初の位置引数 `acc` が含まれます。

[`@force`](@ref) で装飾されたすべての式は、アキュムレーターにプッシュされます。アキュムレーターは、`@forcefun` で装飾されたすべての関数呼び出しの最初の位置引数として追加されます。

# 例

関数定義

```
@forcedef function examplefunction(x1; x2 = 0.1)
    dx = @forcefun otherfunction(x1 - x2)
    @force dx
    return dx^2
end
```

は次のように展開されます。

```
function examplefunction(x1; x2 = 0.1)
    dx = otherfunction(x1 - x2)
    return dx^2
end

function examplefunction(acc, x1; x2 = 0.1)
    dx = otherfunction(acc, x1 - x2)
    push!(acc, dx)
    return dx^2
end
```
