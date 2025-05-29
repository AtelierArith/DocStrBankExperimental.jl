function need*to*interrupt(OutputDir::String)

```
If there is a file named `stop` in folder `OutputDir`, return true; else, return `false`.
```

## Keywords

  * `remove`: if true, remove the `stop` file asynchronously
  * `delay`: if true, wait for 0.1 second to avoid file locking error
