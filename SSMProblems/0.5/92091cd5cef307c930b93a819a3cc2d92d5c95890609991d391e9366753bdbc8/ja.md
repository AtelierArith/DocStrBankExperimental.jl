潜在ダイナミクスの状態空間モデル。

`LatentDynamics`の具体的なサブタイプは、以下に文書化された2つのメソッド、すなわち初期化用と遷移用のメソッドを定義することによって、`logdensity`と`simulate`の関数を実装する必要があります。これらの関数のいずれを実装する必要があるかは、使用する正確な推論アルゴリズムによって異なります。

あるいは、上記のメソッドを定義するために使用される`distribution`関数のメソッドを指定することもできます。

これらのメソッドはすべて、推論時のダイナミクスの依存関係を容易にするために、`kwargs...`を介してキーワード引数を受け入れる必要があります。[制御変数とキーワード引数](@ref)で説明されています。

潜在状態は、ダイナミクスに使用される算術型（例：Float32、ForwardDiff.Dual）から構成される`T`の型である`ET`である必要があります。

# パラメータ

  * `T`: 潜在ダイナミクスの算術型。
  * `ET`: 潜在ダイナミクスの要素型。
