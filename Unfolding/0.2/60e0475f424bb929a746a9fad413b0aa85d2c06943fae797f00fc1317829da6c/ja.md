```
to_vtk(outname, coordinates, props)
```

`coordinates`をVTKポイントとして`outname`.vtuにエクスポートします。オプションで、追加のプロパティは`props`を介して`NamedTuple`または`Dict`として渡され、最初のアイテムがプロパティ名で、2番目がプロパティ値の配列です。
