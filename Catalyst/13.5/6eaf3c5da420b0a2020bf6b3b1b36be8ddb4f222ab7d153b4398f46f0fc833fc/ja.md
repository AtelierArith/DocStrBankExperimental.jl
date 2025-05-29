```
deficiency(rn::ReactionSystem)
```

反応ネットワークの欠損度を計算します。

ここで、$n$ は反応複合体の数、$\ell$ は連結クラスの数、$s$ は階数 $s$ のストイキオメトリック行列を持つネットワークの欠損度 $\delta$ は次のように定義されます。

$$
\delta = n - \ell - s
$$

注意:

  * `reactioncomplexes` への以前の呼び出しによって `rn` に既にキャッシュされている `incidencemat` が必要です。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
δ = deficiency(sir)
```
