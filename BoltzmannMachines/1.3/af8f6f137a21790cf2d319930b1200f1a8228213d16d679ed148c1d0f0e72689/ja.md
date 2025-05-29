`AbstractOptimizer`インターフェースは、最適化手順を指定することを可能にします。これは3つのメソッドで構成されています：

  * `initialized(optimizer, bm)`：これは、ボルツマンマシン`bm`に特化して初期化されたオプティマイザを作成するために使用される場合があります。特に、勾配のための再利用可能なスペースを割り当てるために使用されることがあります。デフォルトの実装は、単に修正されていない`optimizer`を返します。
  * `computegradient!(optimizer, v, vmodel, h, hmodel, rbm)`または`computegradient!(optimizer, meanfieldparticles, gibbsparticles, dbm)`は、正のフェーズと負のフェーズからのサンプルを考慮して勾配を計算するために実装する必要があります。
  * `updateparameters!(bm, optimizer)`は、勾配ステップを取るために指定する必要があります。RBMのデフォルト実装は、`learningrate`と`gradient`フィールドを期待し、与えられたRBMに`learningrate * gradient`を加えます。
