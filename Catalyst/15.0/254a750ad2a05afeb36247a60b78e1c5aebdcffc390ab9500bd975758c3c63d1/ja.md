```
conservationlaw_constants(rn::ReactionSystem)
```

保存則から記号方程式を計算し、保存則定数を従属変数と独立変数の関数として記述します。

注意:

  * 結果の方程式を `rn` にキャッシュするため、次回以降の呼び出しは高速です。

例:

```@julia
rn = @reaction_network begin
    k, A + B --> C
    k2, C --> A + B
    end
conservationlaw_constants(rn)
```

は次のようになります。

```
2-element Vector{Equation}:
 Γ[1] ~ B(t) - A(t)
 Γ[2] ~ A(t) + C(t)
```
