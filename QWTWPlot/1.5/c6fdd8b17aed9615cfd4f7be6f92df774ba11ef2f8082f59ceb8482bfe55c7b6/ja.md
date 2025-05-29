qplot(x::Vector{Float64}, y::Vector{Float64}, name::String, style::String, lineWidth, symSize):: Int32

プロットの通常の線。

# パラメータ:

x と y:   点。 name:       この線の名前。 style: 	 	線の描画方法。 lineWidth:	線の幅。 symSize:	'style'仕様で使用される場合のシンボルのサイズ。 'style'パラメータは何を意味しますか？それは1つまたは2つまたは3つのシンボルを持つ文字列です。 詳細な説明については、2つの場所を見てください：

  * 例のコード  https://github.com/ig-or/QWTWPlot.jl/blob/master/src/qwexample.jl   

      * https://github.com/ig-or/QWTWPlot.jl/blob/master/docs/line-styles.md

この関数は作成された線のIDを返します。おそらく他の関数で使用できます。 IDはすべてが正常であれば >=0 であるべきで、エラーの場合は <0 です。
