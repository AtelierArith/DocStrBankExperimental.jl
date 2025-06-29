```
orient(eph,jd0,time,target,unit,order)
```

ターゲットのエポック jd0+time におけるオリエンテーションのためのオイラー角と導関数を指定された順序まで計算します。補間の精度を最大限に高めるために、時間は2つの浮動小数点数に分割されます。引数 jd0 は整数である必要があり、time は日の小数部分である必要があります。ただし、精度を気にしない場合は、time=0 と jd0（希望する時間）でこの関数を呼び出すことができます。

# 引数

  * `eph`: エフェメリス
  * `jd0::Float64`: jd0+time はエフェメリスに対応する時間座標のためのユリウス日（通常は TDB または TCB）と等しくなければなりません
  * `time::Float64`: jd0+time はエフェメリスに対応する時間座標のためのユリウス日（通常は TDB または TCB）と等しくなければなりません
  * `target::Integer`: オリエンテーションが必要な天体。番号付けシステムは引数 unit に依存します。
  * `unit::Integer` : 結果の単位。この整数は、いくつかの単位定数（unit*）および/または定数 useNaifId の合計です。単位に useNaifId が含まれている場合、ターゲットと中心のために NAIF 識別番号システムが使用されます。単位に useNaifId が含まれていない場合、ターゲットと中心のために古い番号システムが使用されます（関数 compute のドキュメントにあるリストを参照）。単位に outputNutationAngles が含まれている場合、オイラー角の代わりに摂動角が計算されます。
  * `order::Integer` : 導関数の順序

      * 0: 角度のみが計算されます。
      * 1: 角度と1次導関数のみが計算されます。
      * 2: 角度、1次導関数、および2次導関数のみが計算されます。
      * 3: 角度、1次導関数、2次導関数、および3次導関数が計算されます。
