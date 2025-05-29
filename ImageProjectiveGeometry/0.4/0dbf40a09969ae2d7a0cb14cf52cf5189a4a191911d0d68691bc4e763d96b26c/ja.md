quaternionrotate - クォータニオンによって3Dベクトルを回転させる 

```
Usage:   vnew = quaternionrotate(Q, v)

Arguments: Q - [w, xi, yj, zk]の形のクォータニオン
           v - 回転させるベクトル、非同次3ベクトルまたは
               同次4ベクトルのいずれか。
Returns:   vnew - 回転されたベクトル。
```

See also: matrix2quaternion(), quaternion2matrix(), quaternion()
