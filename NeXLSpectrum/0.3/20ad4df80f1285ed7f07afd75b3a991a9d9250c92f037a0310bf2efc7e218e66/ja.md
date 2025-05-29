```
filterfit(unk::FilteredUnknownW, ffs::AbstractVector{FilteredReference}, forcezeros = true)::FilterFitResult
```

未知数をフィルタリングされた参照の配列である ffs に対してフィルターフィットし、結果を FilterFitResult オブジェクトとして返します。デフォルトでは、一般化最小二乗法フィッティング（擬似逆行列実装）を使用します。

この関数は、1つ以上の k 比がゼロ以下の場合にフィットを再実行するように設計されています。負の値に対応する FilteredReference はフィットから削除され、フィットが再実行されます。非正の値の扱いは forcezeros によって決まります。forcezeros=true の場合、非正の値に対する k 比はゼロに設定されます（ただし、不確かさはフィットされたもののままです）。しかし、forcezeros=false の場合、最終的な非正の k 比は関連する不確かさとともに返されます。複数のフィット k 比セットを組み合わせて不確かさを減少させた平均 k 比を生成する場合、forcezeros=false の方が良いです。forcezeros=true は結果を正に偏らせることになります。
