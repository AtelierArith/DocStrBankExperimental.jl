```
draw(g::Graph; resolution = (1920, 1080), nlabels_textsize = 15, arrow_size = 15,
     node_size = 5)
```

ネットワーク図としてグラフを視覚化します。

## 引数

  * `g::Graph`: 視覚化するグラフ。

## キーワード

  * `resolution = (1920, 1080)`: レンダリングされる画像の解像度（ピクセル単位、ネイティブおよびウェブバックエンドに関連）。デフォルトの解像度はHDです。
  * `nlabels_textsize = 15`: 図のラベルのサイズをカスタマイズします。
  * `arrow_size = 15`: 図のエッジを表す矢印のサイズをカスタマイズします。
  * `node_size = 5`: 図のノードのサイズをカスタマイズします。

## 詳細

デフォルトでは、ノードは格納されているデータのタイプとそのユニークIDでラベル付けされます。異なるタイプのデータのラベルをカスタマイズするには、関数 `node_label()` を参照してください。

ネットワーク図をラスタまたはベクター画像としてエクスポートするには、FileIOの `save` を参照してください（バックエンドに応じて）。特定のdpiのエクスポート画像を確保するために、関数 `calculate_resolution()` が役立つ場合があります（物理的なサイズを仮定）。

グラフィックスバックエンドは、Juliaコードが実行されている環境（すなわち、ターミナル、VS CodeなどのIDE、JupyterやPlutoなどのインタラクティブノートブック）と相互作用します。これらの相互作用はすべて、VPLが依存しているグラフィックスパッケージMakieによって制御されます。`draw()` に特有の期待される動作に関する詳細は、一般的なVPLドキュメントに記載されています。

## 戻り値

この関数はMakieの `Figure` オブジェクトを返し、視覚化を副作用として生成します。

## 例

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(1) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> import CairoMakie; # または GLMakie、WGLMakie など。

julia> draw(g);
```
