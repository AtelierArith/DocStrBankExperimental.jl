```
t8_geometry_analytic_new(name, analytical, jacobian, load_tree_data, tree_negative_volume, tree_compatible, user_data)
```

### プロトタイプ

```c
t8_geometry_c * t8_geometry_analytic_new (const char *name, t8_geom_analytic_fn analytical, t8_geom_analytic_jacobian_fn jacobian, t8_geom_load_tree_data_fn load_tree_data, t8_geom_tree_negative_volume_fn tree_negative_volume, t8_geom_tree_compatible_fn tree_compatible, const void *user_data);
```
