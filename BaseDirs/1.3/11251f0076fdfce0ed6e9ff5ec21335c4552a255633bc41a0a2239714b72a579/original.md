**RUNTIME_DIR** (`XDG_RUNTIME_DIR`)

The single base directory relative to which user-specific runtime files and other file objects should be placed. . Applications should use this directory for communication and synchronization purposes and should not place larger files in it.

**Default values**

|            Linux |                          MacOS |        Windows |
| ----------------:| ------------------------------:| --------------:|
| `/run/user/$UID` | `~/Library/ApplicationSupport` | `LocalAppData` |
