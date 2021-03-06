# CHANGELOG

## 1.7.2 - 2018-10-27

- ID Tokens must have a valid "auth_time" claim.
- The signature of an ID Token is now verified even if a prior error occured (thanks [@kanoblake](https://github.com/kanoblake) for reporting the issue and providing a test case)
- Tokens with an invalid signature now throw a `Firebase\Auth\Token\Exception\InvalidSignature` exception.
  It extends the previously thrown `Firebase\Auth\Token\Exception\InvalidToken`,
  so existing behaviour doesn't change.

## 1.7.1 - 2018-01-07

- Fix bug that not more than one custom token could be created at a time.

## 1.7.0 - 2018-01-03

- Cache results from the HTTP Key Store in a PSR-16 cache (default: in memory)
- Deprecated `Firebase\Auth\Token\Handler`.

## 1.6.1 - 2017-07-12

- Add missing `$expiresAt` parameter when creating a custom token with the Handler.

## 1.6.0 - 2017-07-12

- Allow a custom expiration time for custom tokens. 

## 1.5.0 - 2017-04-03

- Allow the usage of a custom key store when using the Handler.

## 1.4.0 - 2017-03-15

- Token verification now includes existence checks for claims (follow up to [kreait/firebase-php#70](https://github.com/kreait/firebase-php/issues/70))

## 1.3.0 - 2017-03-02

- Tokens that seem to be issued in the future now cause a `Firebase\Auth\Token\Exception\IssuedInTheFuture`
  exception. It includes the hint that the system time might not be correct.

## 1.2.1 - 2017-03-01

- Fixed message on UnknownKey exceptions.

## 1.2.0 - 2017-02-28

- Expired tokens now throw a `Firebase\Auth\Token\Exception\ExpiredToken` exception. It
  extends the previously thrown `Firebase\Auth\Token\Exception\InvalidToken`, so
  existing behaviour doesn't change.

## 1.1.1 - 2017-02-19

- Fixed [https://github.com/kreait/firebase-php/issues/65](kreait/firebase-php#65):
  invalid custom token when no claims are given. 

## 1.1.0 - 2017-02-18

- Replaced `StaticKeyStore` with `HttpKeyStore`, which fetches frech Google Public Keys
  each time its `get()` method is invoked. Caching can be implemented by injecting
  an HTTP client with a cache middleware, e.g. 
  [kevinrob/guzzle-cache-middleware](https://github.com/Kevinrob/guzzle-cache-middleware).

## 1.0.1 - 2017-02-07

- Removed non-functional debug header
- Added `"php": "^7.0"`requirement to `composer.json`

## 1.0.0 - 2017-02-05

- Initial release
