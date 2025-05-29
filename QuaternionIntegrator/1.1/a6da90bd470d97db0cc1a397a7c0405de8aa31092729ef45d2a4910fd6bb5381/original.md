```
rotate(q::Quaternion, v)
```

Apply orientation quaternion `q` to rotate vector `v`, return rotated vector.

An object's orientation quaternion rotates vectors from the body-fixed coordinates to world coordinates. For the opposite rotation, call `rotate(inv(q), v)`.
