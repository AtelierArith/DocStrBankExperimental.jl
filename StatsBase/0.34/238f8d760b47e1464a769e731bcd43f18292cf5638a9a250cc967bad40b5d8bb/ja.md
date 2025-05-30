```
countmap(x; alg = :auto)
countmap(x::AbstractVector, wv::AbstractVector{<:Real})
```

`x`内の各ユニークな値をその出現回数にマッピングする辞書を返します。

重みベクトル`wv`が指定されている場合、重みの合計が生のカウントの代わりに使用されます。

`alg`は無重みカウントのみに許可され、次のいずれかである必要があります：

  * `:auto`（デフォルト）：`StatsBase.radixsort_safe(eltype(x)) == true`の場合は`:radixsort`を使用し、それ以外の場合は`:dict`を使用します。
  * `:radixsort`：`radixsort_safe(eltype(x)) == true`の場合は、入力ベクトルをソートするために[基数ソート](https://en.wikipedia.org/wiki/Radix_sort)アルゴリズムを使用します。これは、重複が多い大きな`x`に対して一般的に短い実行時間をもたらします。ただし、基数ソートアルゴリズムは入力ベクトルのコピーを作成し、したがってより多くのRAMを使用します。利用可能なRAMの量が制限されている場合は`:dict`を選択してください。
  * `:dict`：一般的に遅いがRAMを少なく使用する`Dict`ベースのメソッドを使用します。任意のデータ型に対して安全であり、小さな配列に対しては速く、重複があまりない場合は速くなります。
