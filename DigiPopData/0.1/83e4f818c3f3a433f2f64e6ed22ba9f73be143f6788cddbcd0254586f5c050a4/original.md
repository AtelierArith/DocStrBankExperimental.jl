`MetricBinding` is container that binds a **scenario**, an **endpoint** and a concrete `AbstractMetric` description into a single unit that can be logged, displayed or passed to optimisation / validation routines.

# Fields

|       Name |             Type |                                                     Description |
| ----------:| ----------------:| ---------------------------------------------------------------:|
|       `id` |         `String` |                                Unique identifier of the binding |
| `scenario` |         `String` | Scenario (e.g. simulation arm) in which the metric is evaluated |
|   `metric` | `AbstractMetric` |       Metric implementation (`MeanMetric`, `CategoryMetric`, …) |
| `endpoint` |         `String` |          Observable / model variable the metric is computed for |
|   `active` |           `Bool` |              Whether the binding is enabled (`true` by default) |
