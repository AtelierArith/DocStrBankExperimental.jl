```
project_to_U(A::Union{Diagonal,Hermitian}, invW::Hermitian)

project_to_U(A::Union{Diagonal,Hermitian}, invW::Diagonal)
```

これは、エルミート/エルミート行列 `A` を U 空間（Higham 2001 によって定義されたすべての単位対角行列の空間）内の最も近い行列にマッピングします。逆重み行列 `invW` は、各要素を単位対角に調整するためにどれだけ調整するかを決定します。言い換えれば、最も近い相関行列が何であるかを決定するために使用されます。重み行列はエルミート正定値でなければなりません。私たちは W-ノルム（Higham 2001 によって定義された）を使用します。

### 入力

  * `A` - U 空間に投影したい行列
  * `invW` - 逆重み行列。

### 出力

  * `Diagonal` または `Hermitian`。

### 参考文献

Higham, N. J. 2001. ページ335の底部。
