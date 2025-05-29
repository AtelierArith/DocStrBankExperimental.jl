```
HallOfFame(options::AbstractOptions, dataset::Dataset{T,L}) where {T<:DATA_TYPE,L<:LOSS_TYPE}
```

空の HallOfFame を作成します。HallOfFame は `.members` に `PopMember` オブジェクトのリストを格納し、サイズによって列挙されます（すなわち、`.members[1]` は定数解です）。`.exists` は特定のメンバーがインスタンス化されているかどうかを判断するために使用されます。

引数:

  * `options`: 決定論的に関する仕様を含む AbstractOptions。
  * `dataset`: 入力データを含む Dataset。
