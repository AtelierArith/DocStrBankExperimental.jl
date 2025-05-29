```julia
jarvis_march!(hull, points; atol)

```

`points`の凸包を計算し、結果を`hull`に格納します。これは[ジャービスマーチ（ギフトラッピング）アルゴリズム](https://en.wikipedia.org/wiki/Gift_wrapping_algorithm)を使用しています。このアルゴリズムの複雑さは$O(nh)$で、ここで$n$は点の数、$h$は凸包の頂点の数です。
