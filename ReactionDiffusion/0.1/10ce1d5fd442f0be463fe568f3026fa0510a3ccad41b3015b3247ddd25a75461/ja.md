```
get_param(model, turing_params, name, type)
```

与えられた `model` と（潜在的に大きな）パターン形成パラメータセット `turing_params` に対して、この関数は入力 `name` によって指定されたパラメータ値を抽出します。反応パラメータの場合は `type="reaction"` を使用し、拡散定数の場合は `type="diffusion"` を使用します。

例:

```julia
δ₁ = get_param(model, turing_params,"δ₁","reaction")
D_COMPLEX = get_param(model, turing_params,"COMPLEX","diffusion")
```
