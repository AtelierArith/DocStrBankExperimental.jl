```
delrows(A::Union{Matrix, GDtype}; rows::Vector{<:Integer}=Int[], nodata=nothing, col=0)
```

整数のベクトル `rows` にリストされた行または他の条件で見つかった行が削除された新しい行列またはGMTdatasetを返します。

### 引数

  * `A`: 行列またはGMTdataset

### キーワード引数

  * `rows`: 削除する行を指定する整数のベクトル。注意: これまたは `nodata` オプションのいずれかを指定する必要があります。
  * `nodata`: データがない値を示す値。この値が見つかった行は削除されます。NaN値を持つ行を削除するには、$nodata=NaN$ を使用します。注意: これまたは `rows` オプションのいずれかを指定する必要があります。
  * `col`: `nodata` をチェックする列。デフォルトはすべての列を検索します。このオプションを使用すると、特定の列に検索を制限できます。

### 例

```julia
A = [1.0:6 10:10:60];
A[3] = NaN;
M1 = delrows(A, rows=[1,5])
M2 = delrows(M1, nodata=NaN)
M3 = delrows(M2, nodata=40, col=2)
```
