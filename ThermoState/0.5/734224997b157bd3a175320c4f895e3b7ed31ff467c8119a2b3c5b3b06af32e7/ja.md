```
state(;normalize_units=true,check=true,kwargs...)
state(args...;check=true)
state((specs...))
```

引数として渡されたもので `ThermodynamicState` を作成します。引数の1つ以上が `VariableSpec()` の値である場合、作成される状態は呼び出し可能であり、評価されると完全な状態を返します。

`Unitful` の量はSI単位に正規化され、単位が削除されます。これは `normalize_units=false` で無効にできます。

熱力学的状態を作成する際、入力引数はギブスの法則との整合性がチェックされます。このチェックは `check=false` でスキップできます。

仕様のタプルで呼び出された場合、すべてのチェックがスキップされ、コンパイル時に状態を定義することができます。この形式では変数仕様は許可されません。

## 例:

```
st1 = state(t=1,p=2,mass=3) #キーワードインターフェース

t0 = spec(spec"t",1)
p0 = spec(spec"p",2)
mass0 = spec(spec"mass",3)
st2 = state(t0,p0,mass0) #位置引数インターフェース

st3 = state((t0,p0,mass0)) #ランタイムコストなし、チェックなし

st4 = state(t=1,T=2,p=3,P=4) #エラー、エラーをチェックするのに決定的な時間を費やす
st4 = state(t=1,T=2,p=3,P=4,check=false) #エラーなし、チェックしない
```
