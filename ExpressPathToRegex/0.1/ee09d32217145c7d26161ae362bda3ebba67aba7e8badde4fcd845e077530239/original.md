Normalize the given path array, returning a regular expression.

An empty array can be passed in for the keys, which will hold the placeholder key descriptions. For example, using `/user/:id`, `keys` will contain `[{ name: 'id', delimiter: '/', optional: false, repeat: false }]`.
