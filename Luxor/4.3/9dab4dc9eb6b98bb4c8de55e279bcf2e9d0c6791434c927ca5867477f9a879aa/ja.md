```
placeeps(epsfile; log=false)
```

この関数は、以前にCairoによってエクスポートされたEPSファイルを読み込み、解釈します。コマンドは現在の描画に「適用」されます。

主な目的は、EPSベクターグラフィックからいくつかのジオメトリ - 点や曲線など - を抽出することです。

!!! warning
    この関数は「Cairo風」のEPSファイルのみを読み取ります。EPSファイルをエクスポートするすべてのアプリケーションは、プロローグで独自に選択したPostScript関数のセットを定義します。標準はありません。「Cairo風」のEPSプロローグは、CairoからエクスポートされたEPSファイルにハードコーディングされているため予測可能ですが、他のEPSエクスポーターは独自のフレーバーを定義し、誰が知っているPostScript関数を定義して呼び出します。したがって、他のソースからのEPSファイルがこの関数で正常に処理される可能性は低いです。


また、次の点にも注意してください：

  * 現在はクリッピングを無視します。Cairo->EPS->Cairoの変換がどのように機能するかはまだわかりません。
  * 現在は`rectfill`コマンドを無視します - これらは初期のBoundingBoxes/クリッピングのためにしばしば使用されると思いますが、マトリックス変換で使用される場合は、何らかの方法で解釈する必要があります。
  * ブレンドやグラデーション、埋め込まれた画像、埋め込まれたフォントなど、多くの他のものを無視します...

`log`を使用して、コマンドをREPLに印刷し、実行します。

## 例

```julia
@draw begin
    translate(boxtopleft())
    Luxor.placeeps("/tmp/julia.eps")
end
```

SVGファイルをEPSに変換するには、SVGをLuxorに読み込み、EPSとして保存し、その保存したEPSファイルを新しい描画に配置します：

```julia
svgfile = readsvg("julia.svg")
@eps begin
    placeimage(svgfile, centered = true)
end 800 500 "/tmp/julia.eps"
@draw begin
    translate(boxtopleft())
    placeeps("/tmp/julia.eps")
end
```

Luxorコマンドのリストを別のファイルに貼り付けるためのテキストファイルに入れたい場合は、次のように試すことができます（Julia v.1.7以降）。`julia.svg`というSVGがあるとしましょう。

```julia
# SVGを読み込み、EPSとして保存
@eps begin
    svgf = readsvg("julia.svg")
    placeimage(svgf, centered = true)
end 500 500 "/tmp/t.eps"

# EPSをLuxorコマンドに変換
redirect_stdio(stdout = "/tmp/output.jl") do
    placeeps("/tmp/t.eps", log = true)
end

# Luxorコマンドを含めて新しいSVGとして保存：
@svg begin
    translate(boxtopleft())
    include("/tmp/output.jl")
end 500 500 "/tmp/julia.svg"
```
