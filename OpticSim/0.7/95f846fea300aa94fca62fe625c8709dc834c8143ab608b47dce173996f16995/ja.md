```
asphericType(surf::AsphericSurface)
```

`asp`の多項式タイプを照会します。CONIC、ODD、EVEN、またはODDEVENを返します。CONICは非球面項がないことを意味し、ODDは奇数の非球面項のみを持つことを意味し、EVENは偶数の非球面項のみを持つことを意味し、ODDEVENは偶数と奇数の両方の項を持つことを意味します。

この関数は、非球面係数を直接照会する最適化ルーチンによる`surf.aspherics`の適切な解釈を可能にするためのものです。
