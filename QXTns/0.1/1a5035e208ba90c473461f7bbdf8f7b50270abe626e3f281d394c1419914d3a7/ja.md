```
tensor_data(tensor::QXTensor; consider_hyperindices::Bool=false)
```

与えられたテンソルに関連付けられたデータを取得します。consider_hyperindicesフラグがtrueの場合、ハイパインデックスの最初のもののみが保持されます。たとえば、5次元テンソルで2番目と4番目のインデックスがハイパインデックスのグループを形成している場合、このオプションをtrueに設定すると、2番目のインデックスを持つ4次元テンソルが返されます。
