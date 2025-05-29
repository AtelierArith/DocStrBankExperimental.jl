```
multiseparate(img::Array, threshes, score; concavity=0.42, minarea = 10, dump = nothing)
```

複数のしきい値を使用して、画像内の異なるブロブの最良の分離を試みます。最良のブロブ b は、粒子を生成し、より小さな `score(b)` を生成するものとして定義されます。したがって、ブロブを分割すると、より低いスコアの複数のブロブが生成される場合、ブロブは分割されます。デフォルトの関数 'scorer(b::Blob)' は、より円形のブロブを探します。
