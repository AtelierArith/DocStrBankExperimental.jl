```
deficiency(rn::ReactionSystem)
```

反応ネットワークの欠損度を計算します。

ここで、$n$ 反応複合体、$\ell$ リンケージクラス、ランク $s$ のストイキオメトリック行列を持つネットワークの欠損度 $\delta$ は次のように定義されます。

$$
\delta = n - \ell - s
$$

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
δ = deficiency(sir)
```
