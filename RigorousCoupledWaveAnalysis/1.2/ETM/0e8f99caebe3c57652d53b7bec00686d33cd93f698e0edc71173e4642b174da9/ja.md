```
etm_getfields_stack(mdl,grd::RCWAGrid,xypoints,zpoints,λ,a,b,em::Eigenmodes,window,padding)
```

全スタック内の電場と磁場を計算します

# 引数

  * `mdl` : RCWAモデルオブジェクト
  * `grd` : 逆空間グリッドオブジェクト
  * `xypoints` : フィールドを計算するためのx、yのポイント数を指定する二要素ベクトル（偶数でなければならず、そうでない場合は切り捨てられます）
  * `zpoints` : 層の上面に対する希望するz軸ポイントの配列
  * `λ` : 波長
  * `a` : 前方振幅ベクトル
  * `b` : 後方振幅ベクトル
  * `em` : 層の固有モード
  * `window` : ギブス現象に対して使用するウィンドウのタイプ、利用可能：Hann（デフォルト）、None
  * `padding` : xおよびyのウィンドウのパディング、デフォルトは[0,0]

# 出力

  * `efield` : 電場のための4Dテンソル（次元はx、y、z、および成分（E*xまたはE*yまたはE_z）
  * `hfield` : 磁場のための4Dテンソル（次元はx、y、z、および成分（E*xまたはE*yまたはE_z）
