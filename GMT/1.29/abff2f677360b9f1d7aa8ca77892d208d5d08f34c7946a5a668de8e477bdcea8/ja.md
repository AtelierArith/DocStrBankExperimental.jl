```
D = mat2ds(D::GMTdataset, inds::Tuple) -> GMTdataset
```

GMTdataset DをINDSのインデックスでカットしますが、colnamesとTimecol情報を更新します。INDSは行と列の範囲を持つ2つの要素からなるタプルです。例: (:, 1:3) または (:, [1,4,7]) など... 注意してください、元のデータに'Timeinfo'以外の属性があった場合、それらが正しいままである保証はありません。
