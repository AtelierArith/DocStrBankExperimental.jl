```
save_name = henry_result_savename(crystal, molecule, temperature,
                               ljforcefield, insertions_per_volume;
                               comment="")
```

ヘンリー係数を計算中に保存されるファイルの名前を決定します。シミュレーションからの多くの情報を使用して、ファイル名が保持する内容を正確に説明するようにします。

# 引数

  * `crystal::Crystal`: テストされている多孔質結晶
  * `molecule::Molecule`: 結晶内でテストされている分子
  * `temperature::Float64`: シミュレーションで使用される温度 単位: ケルビン (K)
  * `ljforcefield::LJForceField`: 分子間のファン・デル・ワールス力を説明するためにシミュレーションで使用される分子モデル
  * `insertions_per_volume::Union{Int, Float64}`: 単位体積あたりのウィドム挿入の数。作業している結晶に応じてスケーリングされます
  * `comment::AbstractString`: ファイル名に追加されるオプションのコメント
