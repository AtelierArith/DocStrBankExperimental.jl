```julia
triunsuitable!(unsuitable::Function; check_signature)

```

'-u' フラグが設定されている場合に Triangle によって使用される triunsuitable コールバックを設定します。

これは、三角形の頂点の座標を Triangle に渡して、その三角形がさらなる細分化が必要かどうか（すなわち 'true' が返される）を学ぶために呼び出される関数です（'false' が返される）。

ここでは、他のチェック（例えば、最大辺の長さ）も可能です。

この関数の処理は現在スレッドセーフではないことに注意してください。

```
function unsuitable(x1,y1,x2,y2,x3,y3,area)
    myarea=locally_desired_area(x1,y1,x2,y2,x3,y3)
    if area>myarea 
       return true
    else 
       return false
    end
end
```
