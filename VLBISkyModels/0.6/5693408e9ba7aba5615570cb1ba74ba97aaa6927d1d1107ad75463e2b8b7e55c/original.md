Creates a [Kamruddin and Dexter](https://academic.oup.com/mnras/article/434/1/765/1005984) crescent model. This works by composing two disk models together.

# Arguments

  * `router`: The radius of the outer disk
  * `rinner`: The radius of the inner disk
  * `shift`: How much the inner disk radius is shifted (positive is to the right)
  * `floor`: The floor of the inner disk 0 means the inner intensity is zero and 1 means it is a large disk.
