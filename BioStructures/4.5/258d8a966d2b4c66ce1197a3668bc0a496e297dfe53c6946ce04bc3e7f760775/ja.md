```
pdbline(at::Atom)
pdbline(at::DisorderedAtom)
pdbline(at::AtomRecord)
```

`Atom`、`DisorderedAtom`、または `AtomRecord` から `String` として PDB 形式の ATOM または HETATM レコードを形成します。

これは、チェーン ID が 1 文字を超える場合や、原子シリアルが 99999 を超える場合など、値が割り当てられたスペースに収まらないときに `ArgumentError` をスローします。この場合、mmCIF ファイルまたは MMTF ファイルを書き込むために `writemmcif` または `writemmtf` を使用することを検討してください。
