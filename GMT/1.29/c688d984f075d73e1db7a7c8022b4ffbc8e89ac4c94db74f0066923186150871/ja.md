```
sealand(f1::Function, arg1, t1::NamedTuple, f2::Function, arg2, t2::NamedTuple; kw...)
```

と

```
terramar(f1::Function, arg1, t1::NamedTuple, f2::Function, arg2, t2::NamedTuple; kw...)
```

$$
sealand/terramar
$$

の関数ペアは、海側の1つのフィールド（グリッドまたは画像）と、陸上の別のフィールド（同様にグリッドまたは画像）をマッピングする作業を簡素化することを目的としています。この結果を達成するために、私たちは$coast$モジュールと、地球の乾燥部分と湿潤部分をクリップする能力を利用します。最初の関数$sealand$では、最初にモジュール名と海洋地域にプロットされるデータを渡し、次に陸上のモジュールとデータを渡します。2番目の関数$terramar$はその逆を行います。

  * `f1`: データをプロットするために使用されるモジュールの名前。通常、これは$grdimage$または$grdview$であるべきですが、原則として$plot$も使用できます。
  * `arg1`: `f1`モジュールで使用される入力データ。通常、$GMTgrid$、$GMTimage$、$GMTdataset$、または使用するデータのファイル名を含む文字列です。
  * `t1`: `f1`によって消費されるオプションのキーワード=値ペアを持つNamedTuple。
  * `f2`: `f1`と同様ですが、`arg2`に適用されます。
  * `arg2`: `f1`の`arg1`と同様ですが、`f2`用です。
  * `t2`: `f1`の`t1`と同様ですが、`f2`用です。

上記のオプションに加えて、$coast$モジュールで消費される`kw`オプションを渡すことができ、例えば、ペンの色、太さ、スタイルなどのコントロールで海岸線をプロットする結果になります。また、このプログラムに図を完成させて表示するよう指示するために使用することもできます（おなじみの$show=true$）、または図を別の名前/形式で保存するために使用することもできます。*例* $figname="blabla.pdf"$。

### 例: GMTイラストギャラリーの例17を再現する。

```julia
Cgeoid = grd2cpt("@india_geoid.nc");
Cgray  = makecpt(cmap=150, range="-10000,10000", nobg=true);
sealand(grdimage, "@india_geoid.nc", (region="@india_geoid.nc", shade="+d", proj=:Merc,
                                      cmap=Cgeoid, title="Clipping of Images"),
        grdimage, "@india_topo.nc", (shade="+d", cmap=Cgray), shore=0.5)
colorbar!(pos=(inside=true, anchor=:TR, offset=(0.8,0.2), size=(10,0.5), horizontal=true),
          cmap=Cgeoid, xaxis=(annot=5, ticks=1), ylabel=:m, shade=true, show=true)
```
