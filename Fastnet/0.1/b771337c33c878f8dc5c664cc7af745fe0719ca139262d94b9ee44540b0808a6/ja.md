```
healthcheck(net)
```

FastNet *net* の内部整合性チェックを実行します。

所望のパフォーマンスを達成するために、FastNet は一定量の二重記録を行います。理想的な世界では、FastNet 構造は常に内部的に整合性を保つべきです。しかし、ソフトウェアのバグ、CPU やメモリのエラーなど、さまざまな要因から不整合が生じる可能性があります。この関数は、FastNet に保存されている内部データの整合性をチェックし、すべてが正常であることを確認します。

すべてのチェックが通過した場合、戻り値は true であり、そうでない場合は false です。

関連情報は [link](#Fastnet.link) を参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(100,200,10,[])
Network of 0 nodes and 0 links

julia> healthcheck(net);
  Checking repository consistency ... OK
  Checking node accounting ... OK
  Checking link accounting ... OK
  Checking endpoint consistency ... OK
  Checking node stateification ... OK
  Checking link stateification ... OK
```
