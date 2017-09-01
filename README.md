# LV-md5-license-authorizer

To generate and check [MD5](https://en.wikipedia.org/wiki/MD5) based license file based on the MAC address and prefix text.

## Environment

* LabVIEW 2016 Professional Development System 32-bit
* OpenG MD5 Digest Library v4.1 (search and download using VIPM)

## Steps to use the VI set

Please check the usage of each following VI using *Context Help*.

### 1. Generate license file

You can generate license file for the local machine or for the other machine. Use `Generate license file for this machine.vi` to generate for local and `Generate license file for that machine.vi` for other.

The `Generate license file for this machine.vi` use a **prefix text** and the local **MAC address** (fetch automatically) as the information to generate a **MD5 hash**. The MD5 hash would save into the license file `license.dat`. This is the **key** to unlock your program.

If you know the MAC address from the other machine, you can generate the key for that machine using `Generate license file for that machine.vi` with specified MAC address text.

### 2. Bundling license checker into the main VI

Add the `Check license file.vi` into your main VI as the **locker** for your application. Add a VI stop operation for the main VI if the key (license) is invalid.

### 3. Build your main VI as EXE application

Build your main VI as EXE application in order to encrypt your code especially the prefix text. **One can easily crack your application if they know the prefix text.**

## Example

Check the `examples/` for the demonstration.

## Notice

You can customize the license generator and checker for your application by adjusting the input information to generate the MD5 hash in `Build md5.vi`.

## VI list

* License generator:
  * `Generate license file for that machine.vi`
  * `Generate license file for this machine.vi`
* License checker: `Check license file.vi`
* Other tools:
  * `Get Mac address.vi`: get MAC address of the local machine.
  * `Read license file.vi`: read license file and return the content.
