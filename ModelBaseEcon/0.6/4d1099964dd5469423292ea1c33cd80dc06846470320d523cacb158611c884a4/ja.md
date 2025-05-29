```
geteqn(i, ssd::SteadyStateData)
```

i 番目の定常状態方程式を返します。インデックス i は [`alleqns(::SteadyStateData)`](@ref) の出力と同様に解釈されます。`geteqn(i, sdd)` を呼び出すことは `alleqn(ssd)[i]` と同じ効果がありますが、より効率的です。

### 例

```julia
# このようにしてすべての方程式を反復処理します：
for i = 1:neqns(ssd)
    eqn = geteqn(i, ssd)
    # `eqn` と `i` を使って素晴らしいことをする
end
```
