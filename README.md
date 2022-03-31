# audio-example

Quick example on how to wire balena audio block to play a sound.

## Services
**source**

This container uses `sox` to play an audio file. It's configured to send the audio into the audio block on a specific virtual sink.

**audio**

The audio block. The config file creates a virtual sink which we use to receive audio from the source container. Additionally we route the audio from the virtual sink into the device's default hardware audio (typically audio jack on Rasbperry Pi devices) for testing purposes.

__Note__: if you are using a Raspberry Pi4, make sure under `Device Configuration` the `DT Overlay` is set to `"vc4-fkms-v3d"` and **NOT** `"vc4-kms-v3d"`.

**recorder**

This service is not setup but we could use `parecord` for example to grab the audio and pipe it into another program. Just need to configure `PULSE_SERVER` and `PULSE_SOURCE` environment variables.