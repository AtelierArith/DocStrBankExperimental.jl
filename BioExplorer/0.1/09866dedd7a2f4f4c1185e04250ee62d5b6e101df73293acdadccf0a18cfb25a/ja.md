```
sampling_coverage(community_matrix::Community_Matrix)
```

Chaoフレームワークに従って、サンプリングカバレッジの割合を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 種の豊富さデータを含むコミュニティマトリックス。

# 戻り値

  * サンプリングカバレッジの割合。

# 詳細

この関数は、コミュニティ内の全種のうち、サンプリングされた割合を推定するサンプリングカバレッジの割合を計算します。これは、希少種の豊富さを考慮してカバレッジを推定するChaoフレームワークを使用します。出力は、観察データに基づいてサンプリングされた種の割合を表します。

# 参考文献

Chao, A., Kubota, Y., Zelený, D., Chiu, C., Li, C., Kusumoto, B., Yasuhara, M., Thorn, S., Wei, C., Costello, M. J., & Colwell, R. K. (2020). Quantifying sample completeness and comparing diversities among assemblages. Ecological Research, 35(2), 292–314. https://doi.org/10.1111/1440-1703.12102
