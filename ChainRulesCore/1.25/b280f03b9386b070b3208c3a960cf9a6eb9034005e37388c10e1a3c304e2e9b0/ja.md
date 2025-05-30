```
ignore_derivatives(f::Function)
```

ラッパー閉包の勾配を無視するようADシステムに指示します。プライマル計算（フォワードパス）は通常通り実行されます。

```julia
ignore_derivatives() do
    value = rand()
    push!(collection, value)
end
```

これを誤って使用すると、誤った勾配が得られる可能性があります。例えば、次の関数は引数に対してゼロの勾配を持ちます：

```julia
function wrong_grads(x)
    y = ones(3)
    ignore_derivatives() do
        push!(y, x)
    end
    return sum(y)
end
```
