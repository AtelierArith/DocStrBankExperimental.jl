Serialize a `Mechanism` to the [URDF](https://wiki.ros.org/urdf/XML/model) file format.

Limitations:

  * for `<link>` tags, only the `<inertial>` tag is written; there is no support for `<visual>` and `<collision>` tags.
  * for `<joint>` tags, only the `<origin>`, `<parent>`, `<child>`, and `<limit>` tags are written. There is no support for the `<calibration>` and `<safety_controller>` tags.

These limitations are simply due to the fact that `Mechanism`s do not store the required information to write these tags.

Keyword arguments:

  * `robot_name`: used to set the `name` attribute of the root `<robot>` tag in the URDF. Default: `nothing` (name attribute will not be set).
  * `include_root`: whether to include `root_body(mechanism)` in the URDF. If `false`, joints with `root_body(mechanism)` as their predecessor will also be omitted. Default: `true`.
