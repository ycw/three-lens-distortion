# About

Lens ( radial ) distortion  pass for threejs postprocessing. 

[Live example](https://ycw.github.io/three-lens-distortion/example/)



## Installation

via cdn

https://cdn.jsdelivr.net/gh/ycw/three-lens-distortion@{VERSION}/src/index.js

via npm

`$ npm i ycw/three-lens-distortion` or

`$ npm i ycw/three-lens-distortion#{VERSION_TAG}`



## Usage

```js
import * as THREE from 'three'
///
import { EffectComposer } from "three/examples/jsm/postprocessing/EffectComposer";
import { Pass, FullScreenQuad } from "three/examples/jsm/postprocessing/Pass";
/// For Three.js r147 and below, use the following line
/// import { EffectComposer, Pass, FullScreenQuad } from 'three/examples/jsm/postprocessing/EffectComposer'
import { RenderPass } from 'three/examples/jsm/postprocessing/RenderPass'
import { LensDistortionPassGen } from 'three-lens-distortion'

const LensDistortionPass = LensDistortionPassGen({ THREE, Pass, FullScreenQuad }); 
const myLensDistortionPass = new LensDistortionPass({
  distortion: new THREE.Vector2(1., 1.), // radial distortion coeff
  principalPoint: new THREE.Vector2(0., 0.), // principal point coord
  focalLength: new THREE.Vector2(1., 1.), // focal length
  skew: 0. // skew coeff
});

// Add to EffectComposer 
const fx = new EffectComposer(renderer);
fx.addPass(new RenderPass(scene, camera));
fx.addPass(myLensDistortionPass);

// APIs
myLensDistortionPass.distortion.set(.1, .1); // +ve =barrel distortion
myLensDistortionPass.distortion.set(-.1, -.1); // -ve =pincushion distortion
myLensDistortionPass.principalPoint.set(.5, 0); // =shift focus to the right
myLensDistortionPass.focalLength.set(.5, .5); // =closer to camera
myLensDistortionPass.skew = Math.PI / 4; // skew 45d
```



## Credits

[mrdoob / three.js](https://github.com/mrdoob/three.js/)

[Camera Calibration Toolbox for Matlab](http://www.vision.caltech.edu/bouguetj/calib_doc/htmls/parameters.html)




## License

[MIT](./LICENSE)