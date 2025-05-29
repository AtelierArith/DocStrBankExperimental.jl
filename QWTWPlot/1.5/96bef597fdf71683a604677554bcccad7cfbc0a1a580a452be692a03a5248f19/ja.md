qplot1(x::Vector{Float64}, y::Vector{Float64}, name::String, style::String, symSize):: Int32

プロットの線の幅は1です。

```

xとy:   点   
name:       この線の名前   
style: 	 	線の描画方法   
symSize:	記号のサイズ  

```

'style'パラメータは何を意味しますか？これは1つまたは2つまたは3つの記号を持つ文字列です。詳細な説明については2つの場所を参照してください：

  * 例のコード  https://github.com/ig-or/QWTWPlot.jl/blob/master/src/qwexample.jl
  * https://github.com/ig-or/QWTWPlot.jl/blob/master/docs/line-styles.md

この関数は作成された線のIDを返します。おそらく他の関数で使用できるでしょう。 IDはすべてが正常であれば>=0であるべきで、エラーの場合は<0です。
