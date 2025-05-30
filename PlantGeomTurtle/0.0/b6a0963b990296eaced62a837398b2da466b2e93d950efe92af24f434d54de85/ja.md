```
rv!(turtle, strength)
```

タートルをZ軸に向けて回転させます。回転角はタートルの天頂角のコサインに比例します（すなわち、タートルの頭と垂直軸との間の角度）で、`strength`の絶対値がその二つの間の比率になります。`strength`は-1と1の間で変化する必要があります。`strength`が負の場合、タートルは下向きに回転します（すなわち、Z軸の負の値に向かって）、そうでなければ上向きに回転します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> ra!(turtle, 45.0);

julia> rv!(turtle, 0.5);
```
