```
jacobian_matrix(mesh, CI::CartesianIndex)
```

前方変換 (ξ,η,ζ) → (x,y,z) のヤコビ行列を取得します。逆変換 (∂ξ/∂x, ∂ξ/∂y, ...) を取得するには `inv(jacobian_matrix(mesh, idx))` を使用してください。この方法で逆メトリックを見つけることは保守的ではないことに注意してください。たとえば、幾何学的保存法則を観察してください。
