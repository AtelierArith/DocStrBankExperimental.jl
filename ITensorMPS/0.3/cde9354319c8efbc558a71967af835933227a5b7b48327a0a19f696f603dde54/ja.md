```
DMRGObserver(ops::Vector{String},
             sites::Vector{<:Index};
             energy_tol=0.0,
             minsweeps=2,
             energy_type=Float64)
```

DMRGObserverを構築し、`op`関数によって認識される文字列のオペレータ名の配列`ops`を提供します。これらのオペレータは、DMRGの各ステップで各サイトで測定され、その結果は後の分析のためにDMRGOberver内に記録されます。配列`sites`は、DMRG計算のためにMPSおよびMPOを定義するために使用されるサイトの基盤です。

オプションとして、早期停止に使用されるエネルギー許容値と、実行しなければならない最小スイープ数を提供できます。

オプションのキーワード引数：

  * energy_tol: 1回のスイープから次のスイープへのエネルギーがこの量以上に変化しなくなった場合、現在のスイープの後に停止します
  * minsweeps: 少なくともこの数のスイープを実行します
  * energy_type: 各ステップでエネルギーを保存する際に使用する型
