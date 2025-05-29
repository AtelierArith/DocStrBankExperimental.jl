```
centering(sgnum::Integer, D::Integer=3)  -->  Char
```

番号 `sgnum` の空間群の従来のセンタリングタイプ `cntr` を次元 `D` で返します。

センタリングタイプは、ヘルマン-マウグイン記法のラベルの最初の文字に等しく、すなわち `centering(sgnum, D) == first(Crystalline.iuc(sgnum, D))` です。同様に、センタリングタイプはブラヴェタイプの2番目および最後の文字に等しく、すなわち `centering(sgnum, D) == bravaistype(sgnum, D)` です。

次元 `D` に応じて `cntr` の可能な値は次のとおりです（ITA Sec. 9.1.4を参照）：

  * `D = 1`:

      * `cntr = 'p'`: センタリングなし（原始）
  * `D = 2`:

      * `cntr = 'p'`: センタリングなし（原始）
      * `cntr = 'c'`: 面心
  * `D = 3`: 

      * `cntr = 'P'`: センタリングなし（原始）
      * `cntr = 'I'`: 体心（innenzentriert）
      * `cntr = 'F'`: 全面心
      * `cntr = 'A'` または `'C'`: 一面心、(b,c) または (a,b)
      * `cntr = 'R'`: 六角セルがひし形にセンタリングされている
