run_mh(data,model,options)

フィッツ、統計、測定を返します

メトロポリス-ヘイスティングスMCMCアルゴリズムを実行し、結果の統計を計算します

-`data`: AbstractExperimentalData構造体 -`model`: logprior関数を持つAbstractGeneTransitionModel構造体 -`options`: MHOptions構造体

モデルとデータはlikelihoodfn関数を持っている必要があります
