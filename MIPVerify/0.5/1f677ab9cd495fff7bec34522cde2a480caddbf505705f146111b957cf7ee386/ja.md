```julia
read_datasets(name)

```

人気のある機械学習データセットを `NamedTrainTestDataset` として利用可能にします。

# 引数

  * `name::String`: 機械学習データセットの名前。オプション:

      * `MNIST`: [手書き数字のMNISTデータベース](http://yann.lecun.com/exdb/mnist/)。元のデータセットのピクセル値はuint8（0から255）で提供されますが、ここでは0から1の範囲にスケーリングされています。
      * `CIFAR10`: [8000万の小さな画像データセットの10クラスのラベル付きサブセット](https://www.cs.toronto.edu/~kriz/cifar.html)。元のデータセットのピクセル値はuint8（0から255）で提供されますが、ここでは0から1の範囲にスケーリングされています。
