```
route!(g::SchematicGraph, rule::RouteRule,
    nodehook1::Pair{ComponentNode,Symbol}, nodehook2::Pair{ComponentNode,Symbol},
    sty, meta;
    waypoints=[], waydirs=[], global_waypoints=false,
    name=uniquename("r_$(component(nodehook1.first).name)_$(component(nodehook2.first).name)"),
    kwargs...)
route!(g::SchematicGraph, rule::RouteRule, node1::ComponentNode, nodehook2::Pair{ComponentNode,Symbol}, sty, meta; kwargs...)
route!(g::SchematicGraph, rule::RouteRule, nodehook1::Pair{ComponentNode,Symbol}, node2::ComponentNode, sty, meta; kwargs...)
route!(g::SchematicGraph, rule::RouteRule, node1::ComponentNode, node2::ComponentNode, sty, meta; kwargs...)
```

指定されたノードとフックの間に、与えられたスタイル `sty` とメタデータ `meta` を持つ `RouteComponent` を作成します。

`g` 内の結果として得られる `ComponentNode` を返します。

使用例: `route!(g, BSplineRouting(), zline_node=>:feedline, z_launcher_node=>:line, Paths.CPW(10μm, 6μm), GDSMeta(1, 2))`

フックシンボルの1つまたは両方が指定されていない場合、`matching_hook` または `matching_hooks` が使用されて、正しいフックを自動的に見つけることを試みます。

ルートは、`plan!` のようなメソッドが呼ばれるまで、原点に開始点と終了点を持ちます。`waypoints` と `waydirs` はコンポーネントローカル座標であり（`global_waypoints` が `true` でない限り）、`rule` はそれらがどのように使用されるかを決定します。

追加のキーワード引数は、`RouteComponent` のノードの頂点プロパティになります。

`name` は一意である必要があります。
