```
(nav, nav_time) = ExtractNavigator(rawData::RawAcquisitionData, slices::Union{Vector{Int64}, Nothing})
```

MRIReco.jlの生データ構造からナビゲータープロファイルを抽出します。これらは、最初のエコー時間の画像データと同じインデックス（コントラクト、スライス、エンコーディングステップ）で登録されています。ナビゲーター配列とナビゲーター時間配列を返します。ナビゲーター配列は、次の順序で4次元を持っています：k空間サンプル、コイル、k空間ライン、スライス。ナビゲータープロファイルが最初の画像プロファイルの後に取得された場合にのみ有効です。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlで生データを読み込むことで得られる生データ構造
