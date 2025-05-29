y軸の制限を設定します。

y軸の制限は、個別の引数として渡すことも、(**y_min**, **y_max**)のタプルとして渡すこともできます。いずれかの制限を**nothing**に設定すると、データに基づいて自動的に決定されます。これはデフォルトの動作です。

:param y*min: 	- y軸の下限、または 	- 自動的な下限を使用するための**nothing**、または 	- 両方のy軸の制限のタプル :param y*max: 	- y軸の上限、または 	- 自動的な上限を使用するための**nothing**、または 	- 最初の引数として両方のy軸の制限が渡された場合は**nothing** :param adjust: 制限が調整されるかどうか

**使用例:**

.. code-block:: julia

```
julia> # y軸の制限を-1と1に設定
julia> ylim((-1, 1))
julia> # y軸の制限を自動的に決定されるようにリセット
julia> ylim()
julia> # y軸の上限をリセットし、下限を0に設定
julia> ylim((0, nothing))
julia> # y軸の下限をリセットし、上限を1に設定
julia> ylim((nothing, 1))
```
