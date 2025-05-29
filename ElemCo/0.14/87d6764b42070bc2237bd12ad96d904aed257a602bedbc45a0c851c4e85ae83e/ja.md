```
@freeze_orbs(freeze_orbs)
```

積分において、配列または範囲 `freeze_orbs` に従って軌道を凍結します。

また、軌道は、例えば "1-5+7-8" や "1:5;7-8" のように、+/- または :/; 構文を使用して文字列として指定することもできます。

# 例

```julia
fcidump = "FCIDUMP"
@freeze_orbs 1:5
...
@ECinit
@freeze_orbs [1,2,20,21]
```
