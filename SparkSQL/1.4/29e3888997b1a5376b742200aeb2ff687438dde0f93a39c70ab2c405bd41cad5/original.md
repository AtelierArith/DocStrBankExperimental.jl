# Purpose

Submits application to Apache Spark cluster.

# Arguments

  * `master::String`: the URL to the Spark cluster master.
  * `appName::String`: the name of the application.

# Examples

Basic spark session:

```
spark = SparkSession("spark://example.com:7077", "Julia SparkSQL Example App")
```
