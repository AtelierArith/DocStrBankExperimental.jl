```
lattice(V::AbstractSpace, basis::MatElem ; check::Bool = true) -> AbstractLat
```

与えられた環境空間 `V` と行列 `basis` に対して、`basis` の行によって生成される格子を `V` 内で返します。`V` がエルミート（または二次）である場合、出力はエルミート（または二次）格子になります。

デフォルトでは、`basis` がフルランクであることが確認されます。このテストは、`check` を false に設定することで無効にできます。
