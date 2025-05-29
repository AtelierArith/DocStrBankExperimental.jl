重みを新しい重みにマッピングする表現。

重み `w(x)dx` とマップ `y=m(x)` が与えられたとき、マッピングされた重みは `w(m(x))/J(m(x))dx` と定義されます。ここで `J` は `m` のヤコビ行列式です。

定義は、変数変換の後に次の等式が成り立つようになっています：

integral(t->f(t), domain, weight) =     integral(t -> f(inverse(m,t))), m.(domain), MappedWeight(m, weight)
