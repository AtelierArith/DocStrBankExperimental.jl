```
setinvalid_qualityflag!(df; 
  vars=["LE","H","NEE","Tair","VPD","wind"],
  qc_suffix="_qc",
  good_quality_threshold = 1.0,
  missing_qc_as_bad = true,
  setvalmissing = true, 
)

品質フラグに問題を示すレコードを :valid 列で false に設定します。

# 引数

  * df: :GPP 列を持つ DataFrame

オプション

  * `vars=["LE","H","NEE","Tair","VPD","wind"]`: 品質をチェックする列
  * `qc_suffix="_qc"`: 対応する品質フラグ列の命名
  * `good_quality_threshold = 1.0`: データが良好な品質と見なされる品質フラグの閾値
  * `missing_qc_as_bad = true`: 品質フラグが欠損しているレコードを無効としてマークしない場合は false に設定
  * `setvalmissing = true`: 問題のある品質フラグに対応する値列の値を欠損に置き換えないようにするには false に設定。

# 値

修正された :valid および値列を持つ df。

# 例

```

jldoctest; output = false using DataFrames df = DataFrame(   NEE = 1:3, NEE*qc = [1,1,2],   GPP = 10:10:30, GPP*qc = [1,missing,1]) setinvalid_qualityflag!(df; vars = ["NEE", "GPP"]) df.valid == [true, false, false] ismissing(df.GPP[2]) && ismissing(df.NEE[3])

# output

true ```
