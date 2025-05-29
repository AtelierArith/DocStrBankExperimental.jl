```
write_hinfile(
    fname::AbstractString,
    ac::AtomContainer
)
```

アトムコンテナをHyperChem HINファイルとして保存します。

!!! note
    HINファイルは、分子グラフ内の接続された成分として分子を定義します。AtomContainerに結合が欠けている場合、例えばPDBファイルを読み込んだ後に正しく後処理を行わなかった場合、HINファイルには驚くほど多くの分子が含まれる可能性があります。

