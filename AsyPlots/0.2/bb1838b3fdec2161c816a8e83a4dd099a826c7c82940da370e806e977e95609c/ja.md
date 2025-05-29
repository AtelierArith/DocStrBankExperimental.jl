```
Arrow(name::AbstractString,
      size::Real,
      position::Real)
```

矢印を描画するための指示を保存します

`position` は [0,1] の要素で、矢印がパスに沿ってどれだけ描画されるべきかを示します

NoArrow() は矢印なしの指示を返し、Arrow3() は3Dパスに適した矢印を提供します
