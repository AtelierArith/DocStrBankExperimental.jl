```
bricklayertopology(nqubits::Integer; periodic=false)
```

`nqubits`量子ビット上のいわゆる1Dブリックレイヤー回路のトポロジーを作成します。これは、奇数-偶数および偶数-奇数量子ビットインデックスをそれぞれ接続する2つのサブレイヤーで構成されています。`periodic`が`true`に設定されている場合、最後の量子ビットは最初の量子ビットに接続されます。
