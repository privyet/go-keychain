# Go Keychain

A library for accessing the Keychain for OSX and iOS.

Requires Mac OSX 9 or greater and iOS 7 or greater.

**WARNING**: This is still being tested and reviewed.

## Usage

```go
item := keychain.NewGenericPassword(
  "MyService",
  "gabriel",
  []byte("toomanysecrets"),
  "com.mycorp",
  keychain.SynchronizableNo,
  keychain.AccessibleWhenUnlockedThisDeviceOnly)

err := keychain.AddItem(item)
if err == KeychainErrorDuplicateItem {
  // Duplicate
}

accounts, err := keychain.GetAccounts("MyService")
// Should have 1 account == "gabriel"

err := keychain.DeleteGenericPasswordItem("MyService", "gabriel")
if err == KeychainErrorNotFound {
  // Not found
}
```
