状態空間モデルのための抽象型。

`AbstractStateSpaceModel` の具体的なサブタイプは、前方シミュレーションを実行する `AbstractMCMC.sample` のメソッドを実装する必要があります。実装の例については、[AbstractMCMC.sample(::StateSpaceModel)](@ref) を参照してください。

ほとんどの一般的な使用ケースでは、以下に文書化されている定義済みの `StateSpaceModel` 型で十分です。
