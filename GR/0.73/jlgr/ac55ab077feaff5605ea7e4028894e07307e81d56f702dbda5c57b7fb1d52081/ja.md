x軸の制限を設定します。

x軸の制限は、個別の引数として渡すことも、(**x_min**, **x_max**)のタプルとして渡すこともできます。いずれかの制限を**nothing**に設定すると、データに基づいて自動的に決定されます。これはデフォルトの動作です。

:param x*min: 	- x軸の下限、または 	- 自動的な下限を使用するための**nothing**、または 	- 両方のx軸の制限のタプル :param x*max: 	- x軸の上限、または 	- 自動的な上限を使用するための**nothing**、または 	- 最初の引数として両方のx軸の制限が渡された場合は**nothing** :param adjust: 制限が調整されるかどうか

**使用例:**

.. code-block:: julia

```
julia> # x軸の制限を-1と1に設定
julia> xlim((-1, 1))
julia> # x軸の制限を自動的に決定されるようにリセット
julia> xlim()
julia> # x軸の上限をリセットし、下限を0に設定
julia> xlim((0, nothing))
julia> # x軸の下限をリセットし、上限を1に設定
julia> xlim((nothing, 1))
```
