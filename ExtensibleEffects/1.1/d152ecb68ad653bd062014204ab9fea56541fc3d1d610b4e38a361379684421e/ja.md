```
@syntax_eff_noautorun begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```

`autorun` ルーチンを実行しない拡張可能な効果の構文。 `@syntax_eff` と同様に、 `@pure` で前置きされていないすべての値に `effect` を適用し、それらを `Eff` モナドに持ち上げます。 結果は、それぞれの `Eff` モナド上で `@syntax_flatmap` を使用して結合され、直接返されます。

## 例

```julia
unhandled_eff = @syntax_eff_noautorun begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end

mycustomwrapper(i::Int) = collect(1:i)
# モナディックのような構文で、未処理の効果を解釈する前にラッパーを適用します
unhandled_eff = @syntax_eff_noautorun mycustomwrapper begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```
