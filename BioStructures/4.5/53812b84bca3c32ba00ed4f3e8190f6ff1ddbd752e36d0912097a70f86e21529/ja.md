```
resid(res; full=true)
```

`AbstractAtom` または `AbstractResidue` のための記述的な残基 ID `String` を取得します。

形式は残基番号の後に挿入コードが続き、ヘテロ残基の場合はその前に "H*" が付加されます。`full` が `true` の場合、チェーン ID もコロンの後に追加されます。例としては "50A"、"H*20"、および "10:A" があります。
