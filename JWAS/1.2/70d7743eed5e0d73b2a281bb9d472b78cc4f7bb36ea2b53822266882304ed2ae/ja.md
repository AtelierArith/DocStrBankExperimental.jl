```
GWAS(marker_effects_file,model;header=true,window_size=100,threshold=0.001)
```

マップファイルなしでゲノムウィンドウベースのGWASを実行します

  * マーカー効果のMCMCサンプルは、区切り文字が','の**marker*effects*file**に保存されます。
  * **window_size**は、定数（各ウィンドウ内のマーカー数が同じ）または各ウィンドウ内のマーカー数の配列です。
  * **model**は、分析に使用されるmodel::MMEまたは遺伝型共変量行列M::Arrayです。
  * ファイル形式:
