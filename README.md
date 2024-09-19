# Setting up QEMU for ARM

## 1. Install QEMU

### On Ubuntu/Debian:
```
sudo apt update
sudo apt install qemu-system-arm
```

### On macOS (using Homebrew):
```
brew install qemu
```

### On Windows:
- Download the QEMU installer from the official website: https://www.qemu.org/download/#windows
- Run the installer and follow the prompts

## 2. Verify Installation
Open a terminal/command prompt and run:
```
qemu-system-arm --version
```

## 3. Download an ARM system image
For beginners, Debian ARM images are recommended:
- Visit: https://people.debian.org/~aurel32/qemu/
- Download an ARM image (e.g., `debian-squeeze-armel-small.qcow2`)

## 4. Run QEMU with the ARM image
```
qemu-system-arm -M versatilepb -kernel vmlinuz-2.6.32-5-versatile -initrd initrd.img-2.6.32-5-versatile -hda debian-squeeze-armel-small.qcow2 -append "root=/dev/sda1"
```

Note: Adjust filenames if you downloaded different versions.

## 5. Additional Tools
- Install cross-compilation tools:
  ```
  sudo apt install gcc-arm-linux-gnueabi
  ```

## 6. Write and Compile ARM Assembly
1. Create a file `hello.s` with your ARM assembly code
2. Compile: `arm-linux-gnueabi-as hello.s -o hello.o`
3. Link: `arm-linux-gnueabi-ld hello.o -o hello`
4. Run in QEMU: `qemu-arm ./hello`

Remember to adjust commands based on your specific setup and requirements.
