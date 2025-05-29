```
conservedequations(rn::ReactionSystem)
```

保存則から記号的方程式を計算し、従属変数を独立変数および保存則定数の関数として書きます。

注意:

  * 結果の方程式を `rn` にキャッシュするため、次回以降の呼び出しは高速です。

例:

```@repl
rn = @reaction_network begin
    k, A + B --> C
    k2, C --> A + B
    end
conservedequations(rn)
```

は次のようになります

```
2-element Vector{Equation}:
 B(t) ~ A(t) + Γ[1]
 C(t) ~ Γ[2] - A(t)
```
