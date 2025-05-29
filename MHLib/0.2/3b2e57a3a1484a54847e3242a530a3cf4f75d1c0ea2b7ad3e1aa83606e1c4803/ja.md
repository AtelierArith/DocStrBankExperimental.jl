```
fillup!(::SubsetVectorSolution, pool, random_order)
```

プールから要素をスキャンし、選択の可否があるものを選択します。

`pool`内の要素はまだ選択されていない必要があります。パラメータ`pool`は、何も指定されていない場合、`x[sel+1:end]`が`pool`として使用されるか、`sel`より大きい`_`のための`x[sel+1:_]`である必要があります。`random_order`が設定されている場合、プール内の要素はランダムな順序で処理されます。`element_added_delta_eval()`を使用します。選択された要素が`pool[begin:return-value]`に表示されるように、`pool`内の要素の順序を変更します。
