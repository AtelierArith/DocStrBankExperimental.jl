```
duallagrangec0d1(originalmesh, refinedmesh)
```

ユーザーは同じオブジェクトを表す2つのメッシュを提供する責任があります。2つ目のメッシュは「barycentric_refinement(originalmesh)」を使用して取得する必要があります。この基底関数は双対ラグランジュ基底関数を作成し、形状の配列[fns]を含むオブジェクトを返します。また、洗練されたメッシュを含むジオメトリも返します。
