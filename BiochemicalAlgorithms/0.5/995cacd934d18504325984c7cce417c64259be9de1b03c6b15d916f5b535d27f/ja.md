```
translate!(::AtomTable{T}, t::Vector3{T})
translate!(::AbstractAtomContainer{T}, t::Vector3{T})
```

与えられた変換ベクトル `t` に従って、指定されたコンテナのすべての原子を移動します。
