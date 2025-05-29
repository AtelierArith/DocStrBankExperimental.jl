```
オプティマイザ
```

Optim.jlのラッパーで、StateSpaceModels.jlでオプティマイザの選択を簡単にします。ユーザーは、Optim.jlのすべての適切なオプティマイザの中から非常に似た構文を使用して選択できます。

# 例

```@jldoctest
julia> using Optim

# 大きなログを表示しないようにセミコロンを使用
julia> opt = Optimizer(Optim.LBFGS(), Optim.Options(show_trace = true));
```
