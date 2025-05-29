```
updatelocalpdb(; dir::AbstractString=pwd(), format::Type=PDBFormat)
```

ローカルのタンパク質データバンク（PDB）のコピーを更新します。

新しい、修正された、そして廃止されたPDBエントリの最近の週次リストを取得し、指定された`format`のPDBファイルをローカルの`dir`ディレクトリ内で自動的に更新します。インターネット接続が必要です。
