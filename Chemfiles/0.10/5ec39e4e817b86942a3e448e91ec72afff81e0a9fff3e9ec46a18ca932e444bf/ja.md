```julia
remove_atom!(frame::Chemfiles.Frame, index::Integer)

```

`index`の`atom`を`frame`から削除します。

この関数は、`index`の後のすべての`atoms`のインデックスを変更し、`positions`または`velocities`を使用して取得した配列を無効にします。
