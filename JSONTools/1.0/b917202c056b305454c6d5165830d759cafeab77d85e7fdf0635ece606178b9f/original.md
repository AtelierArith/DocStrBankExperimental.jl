JSONPath is used to access and set the data in JSON serializable objects using indexing. Below is the list of propertie of the JSONPath object:

## Properties that define the path

  * `path` - A Tuple of keys and indices that defines the path to the value.

## Properties that spefify how to handle inserting data

  * `parents` - If true, the path will be created if it doesn't exist.
  * `candestroy` - If true, the path will be overwritten if it exists (including the parent values that are in the way).
  * `canfilllists` - If true, the path will be created if it doesn't exist and the lists will be filled with the listfiller function.
  * `listfiller` - This function is used to fill the lists when canfilllists is true.
