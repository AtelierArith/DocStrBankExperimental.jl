```
DirectCall{KeyType,TimeType,TreeType}()
```

DirectCallは、指数分布の中からサンプリングする役割を担っています。これは、ダイレクトメソッドを使用してサンプリングを行います。この場合、ダイレクトメソッドに対する最適化は行われていないため、呼び出すたびにすべてを再計算するため、DirectCallと呼ばれています。

ダイレクトメソッドのアルゴリズムは、ハザードレートのリストを維持するために使用するデータ構造に大きく依存しており、それによってハザードの合計を知り、ランダムな値を使用してそれらにインデックスを付けることができます。この構造体には、デフォルトのコンストラクタがあり、あなたのためにデータ構造を選択しますが、いくつかのオプションがあります。

# 例

シミュレーションで使用する異なるクロックキーの数が少ないことがわかっている場合、リストから削除するのではなく、ゼロにしてクロックを無効にするデータ構造を使用することが理にかなっています。これにより、メモリのチャンジが大幅に減少します。これは、基盤となるデータ構造を変更することで実現できます。

```julia
prefix_tree = BinaryTreePrefixSearch{T}()
keyed_prefix_tree = KeyedKeepPrefixSearch{K,typeof(prefix_tree)}(prefix_tree)
sampler_noremove = DirectCall{K,T,typeof(keyed_prefix_tree)}(keyed_prefix_tree)
```
