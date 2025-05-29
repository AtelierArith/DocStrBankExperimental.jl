```
space(::SiteType"Fermion";
      conserve_qns=false,
      conserve_nf=conserve_qns,
      conserve_nfparity=conserve_qns,
      qnname_nf = "Nf",
      qnname_nfparity = "NfParity",
      qnname_sz = "Sz",
      conserve_sz = false)
```

"フェルミオン"タイプのサイトのヒルベルト空間を作成します。

オプションで、保存される対称性とその量子数ラベルを指定します。
