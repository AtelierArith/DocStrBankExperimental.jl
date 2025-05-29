```
bootsnaq(T::HybridNetwork, df::DataFrame)
bootsnaq(T::HybridNetwork, vector of tree lists)
```

SNaQのブートストラップ分析。ブートストラップデータは、データフレーム`df`に与えられた信頼区間内で均等にサンプリングされたクワルテットの一致係数（CF）である可能性があります。あるいは、ブートストラップデータは、ツリーリストのベクトルからサンプリングされた遺伝子ツリーである可能性があります：ローカスごとに1つのブートストラップツリーのリスト（これを生成するには、`PhyloNetworks`の[`readmultinewick_files`](https://juliaphylo.github.io/PhyloNetworks.jl/stable/lib/public/#PhyloNetworks.readmultinewick_files-Tuple{AbstractString})を参照してください）。ブートストラップファイルのリストを含むファイルからです。

各ブートストラップ複製から、ネットワークは[`snaq!`](@ref)を使用して推定され、トポロジー`T`から検索が開始されます。オプションの引数には、デフォルト値が括弧内に示されています：

  * `hmax` (1): 推定されたネットワークの最大リチュレーション数
  * `nrep` (10): ブートストラップ複製の数
  * `runs` (10): 各複製のための独立した最適化ランの数
  * `filename` ("bootsnaq"): 出力ファイルのルート名。""の場合は出力ファイルなし。
  * `seed` (0で時計からランダムシードを取得): ランダム数生成器のシード
  * `otherNet` (空): 各複製が`otherNet`でprcnet%のランを開始し、`T`で(1-prcnet)%のランを開始するための別の開始トポロジー
  * `prcnet` (0): `otherNet`で開始するランの割合；0.0以外の場合はエラー、かつ`otherNet`が指定されていない場合。
  * `ftolRel`, `ftolAbs`, `xtolRel`, `xtolAbs`, `liktolAbs`, `Nfail`, `probST`, `verbose`, `outgroup`: `snaq!`を参照、同じデフォルト。

`T`がツリーである場合、その枝の長さは最初に[`updateBL!`](@ref)を使用して大まかに最適化されます（各枝を定義するすべてのクワルテットの平均CFを使用し、このクワルテットCFに対応する共alescent単位を計算します）。`T`に1つ以上のリチュレーションがある場合、その枝の長さは検索を開始するためにそのまま使用されます。`otherNet`の枝の長さは、検索を開始するために常にそのまま使用されます。
