```
FEMatrix{TvM,TiM}(FESX, FESY; name = "auto")
```

FESXとFESYが単一のFESpaceである場合、FEMatrixを1つの長方形ブロック（FESX、FESY）で作成します。また、FESXとFESYのFESpaceベクトルのエントリに対応するブロックを持つ長方形ブロック行列を作成します。オプションで、行列の名前を指定できます。
