```
testplot(model, args...; kwargs...)
```

`model`のテスト特性のプロットを作成します。

結果のプロットには、テスト特性曲線/期待スコア（左）とテスト情報曲線（右）が含まれます。

追加の`args...`と`kwargs...`は、下位レベルのプロット関数[`expected_score_plot`](@ref)と[`information_plot`](@ref)に渡されます。
