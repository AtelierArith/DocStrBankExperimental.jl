```
zetaplot!(f::Indexable, pr::MixedModelProfile;
          absv=false,
          ptyp='β',
          coverage=[.5,.8,.9,.95,.99],
          zbd=nothing)
```

パラメータ `ptyp` に基づいて `pr` から `f` へのプロファイル ζ（またはその絶対値）のプロットを持つ軸を追加します。

有効な `ptyp` 値は 'β'、'σ'、および 'θ' です。

`absv` が `true` の場合、`coverage` のカバレッジレベルに対応する区間が各パネルに追加されます。
