Obtain the `SQLStore.Table` object corresponding to the table `name` in database `db`.

The returned object supports:

  * `SELECT`ing rows with `collect`, `filter`, `first`, `only`. Random row selection: `sample`, `rand`.
  * `UPDATE`ing rows with `update!`, `updateonly!`, `updatesome!`.
  * `DELETE`ing rows with `delete!`, `deleteonly!`, `deletesome!`.
  * `INSERT`ing rows with `push!`, `append!`.
  * Retrieving metadata with `schema`, `columnnames`, `ncol`.
  * Other: `nrow`, `length`, `count`, `any`.
