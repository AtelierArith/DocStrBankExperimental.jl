X、Y、または Z 軸の目盛りの間隔を設定します。

対応する軸のために `xticks`、`yticks` または `zticks` 関数を使用します。

:param minor: マイナー目盛りの間隔。 :param major: （オプション）メジャー目盛りの間のマイナー目盛りの数。

**使用例:**

.. code-block:: julia

```
julia> # X 軸の 0.2 単位ごとのマイナー目盛り
julia> xticks(0.2)
julia> # Y 軸の 1 単位ごとのメジャー目盛り（5 のマイナー目盛り）
julia> yticks(0.2, 5)
```
