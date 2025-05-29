```
bool = check_ped(pedlist [, parentsfirst, warning])
```

系譜リストに明らかなエラーがないかをチェックします。系譜リスト `pedlist` は、ファイルから `ReadPedigree` で生成された整数行列です。この関数は以下のエラーをチェックします。

  * 父（または母）が母（または父）として現れる。
  * リストにループがある。すなわち、動物の祖先がその動物の子孫でもある。
  * 親がその子孫の前に出ている。すなわち、IDが時間的にソートされている（オプション； `parentsfirst=true` でチェック）。

エラーがない場合は `true` を返し、エラーがある場合はエラーメッセージと共に `false` を返します（`warining=false` で省略可能）。

### 例

```jldoctest
julia> using PedigreeTools;

julia> pedlist,idtable = read_ped("pedigree.txt");

julia> check_ped(pedlist)
true

# 親がその子孫の前に出ているかをチェック
julia> check_ped(pedlist, parentsfirst=true)
true
```
