```
dcm2euler(dcm, order::Symbol = :body2nav)
```

DCM（方向コサイン行列）をヨー、ピッチ、ロールのオイラー角に変換します。ここでのヨーは方位角および見出しと同義です。使用例は2つあります。

1. `order = :body2nav`の場合、提供されたDCMは標準の-ロール、-ピッチ、-ヨーの順序でボディフレームからナビゲーションフレームに回転するものと仮定されます。たとえば、v1がボディフレームの3x1ベクトル[nose, right wing, down]である場合、そのベクトルがナビゲーションフレーム[north, east, down]に回転すると、v2 = dcm * v1となります。
2. `order = :nav2body`の場合、提供されたDCMは標準のヨー、ピッチ、ロールの順序でナビゲーションフレームからボディフレームに回転するものと仮定されます。たとえば、v1がナビゲーションフレームの3x1ベクトル[north, east, down]である場合、そのベクトルがボディフレーム[nose, right wing, down]に回転すると、v2 = dcm * v1となります。

参考文献: Titterton & Weston, Strapdown Inertial Navigation Technology, 2004, セクション3.6（ページ36-41および537）。

**引数:**

  * `dcm`:   `3` x `3` x `N` 方向コサイン行列 [-]
  * `order`: （オプション）回転順序 {`:body2nav`,`:nav2body`}

**戻り値:**

  * `roll`:  長さ-`N` ロール角 [rad]、x軸周りの右手系回転
  * `pitch`: 長さ-`N` ピッチ角 [rad]、y軸周りの右手系回転
  * `yaw`:   長さ-`N` ヨー角 [rad]、z軸周りの右手系回転

```
