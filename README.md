# Generate time-based one time passwords given a token

This program generates a time-based one time password (T-OTP) for the provided OTP token.

## Prequisites

[Golang](https://golang.org) - tested with Go version 1.13.4.

[github.com/atotto/clipboard](https://github.com/atotto/clipboard)

```go get github.com/atotto/clipboard```

## Building

You may build this program by running:

```
go build
```

## Usage

```
$ totp -h
Usage: totp
  -otp_token string
    	OTP Token
  -output_clipboard
    	Copy OTP value to clipboard
  -output_stdout
    	Print OTP value (default true)
```

### Examples:

Run `totp` and have OTP copied to clipboard but not printed to STDOUT. OTP token is provided as a string.
```
$ totp -otp_token=abcdefghijklmnop \
    -output_clipboard=true
    -output_stdout=false
```

Run `totp` and have OTP sent to STDOUT but not copied to clipboard (this is the default output). OTP token has spaces which are removed when parsed.
```
$ totp -otp_token="abc def ghi jkl mno p"
```

Run `totp` with OTP token retrieved via LastPass CLI and have the OTP sent to clipboard and STDOUT.
```
$ otp -otp_token=$(lpass show --field=otp_token "AWS") \
    -output_clipboard=true
```
