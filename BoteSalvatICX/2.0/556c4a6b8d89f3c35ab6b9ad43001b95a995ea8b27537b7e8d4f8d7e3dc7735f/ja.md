```
ionizationcrosssection(
     z::Int,
     subshell::Int,
     energy::AbstractFloat,
     edgeenergy::AbstractFloat = edgeenergy(z, subshell),
 )
```

エネルギーのある電子に対する内側サブシェルのイオン化断面積を計算します。`z` または `subshell` が範囲外である場合はアサートします。要素/サブシェルのペアが利用可能かどうかを判断するには、hasedge(...) を使用してください。

  * `z` : 範囲 1:99 の原子番号 z
  * `subshell` : イオン化される原子サブシェル 1->K, 2->L₁, 3->L₂, ..., 9->M₅
  * `energy` : 入射電子の運動エネルギー (eV)
  * `edgeenergy` : サブシェルのエッジエネルギー (eV)
