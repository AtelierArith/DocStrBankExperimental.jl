```
imaginary_stability_interval(tab::ODERKTableau;
                             initial_guess = length(tab) - 1)
```

虚数安定区間の長さ、すなわち虚数軸上の安定領域のサイズを計算します。詳細は[`stability_region`](@ref)を参照してください。
