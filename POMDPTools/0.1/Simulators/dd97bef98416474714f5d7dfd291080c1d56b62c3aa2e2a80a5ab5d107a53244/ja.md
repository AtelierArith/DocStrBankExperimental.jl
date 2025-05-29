```
for t in eachstep(hist, [spec])
    ...
end
```

`SimHistory` `hist`のステップを反復処理します。`spec`は、各ステップで返される内容を制御するシンボルまたは文字列のタプルです。

例えば、

```julia
for (s, a, r, sp) in eachstep(h, "(s, a, r, sp)")    
    println("reward $r received when state $sp was reached after action $a was taken in state $s")
end
```

は、シミュレーションの各ステップに対して開始状態、アクション、報酬、および遷移先状態を返します。

また、ステップを暗黙的に展開する代わりに、ステップの要素にフィールドとしてアクセスすることもできます（各ステップは`NamedTuple`です）：

```julia
for step in eachstep(h, "(s, a, r, sp)")    
    println("reward $(step.r) received when state $(step.sp) was reached after action $(step.a) was taken in state $(step.s)")
end
```

反復仕様での有効な要素は次の通りです。

  * (PO)MDP動的意思決定ネットワーク内の任意のノード（デフォルトでは`:s`, `:a`, `:sp`, `:o`, `:r`）
  * `b` - ステップにおける初期の信念（POMDPのみ）
  * `bp` - `o`に基づいて更新された後の信念（POMDPのみ）
  * `action_info` - ポリシー決定からの情報（`action_info`から）
  * `update_info` - 信念更新からの情報（`update_info`から）
  * `t` - タイムステップインデックス
