```
select_point(scene; kwargs...) -> point
```

2D `scene` 上で左マウスボタンをクリックし、ドラッグしてからクリックを解除することで、インタラクティブにポイントを選択します。選択されたポイントに対応する値を持つ**observable**を返します。さらに、この関数はユーザーがクリックしてマウスを動かすと、シーン上にポイントを*プロット*します。ボタンがもうクリックされていないとき、プロットされたポイントは消えます。

返されるポイントの値は、ユーザーがクリックを解除したときに**のみ**更新されます。

`kwargs...`は、選択されたポイントをプロットする`scatter!`に伝播されます。
