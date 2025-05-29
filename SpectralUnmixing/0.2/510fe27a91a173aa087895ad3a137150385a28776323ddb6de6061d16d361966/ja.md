```
plot_endmembers_individually(endmember_library::SpectralLibrary;
output_name::String="", legend_on::Bool=false)
```

スペクトルライブラリから各エンドメンバーのスペクトルをクラスごとに個別にプロットします。

  * 各クラスのために別々のプロットを作成し、凡例はデフォルトで無効になっています。
  * `output_name`が提供されている場合はファイルを保存し、そうでない場合は保存しません。
