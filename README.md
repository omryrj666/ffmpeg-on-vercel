# FFmpeg on Vercel 🎥🚀

[![Download Releases](https://img.shields.io/badge/Download%20Releases-blue?style=for-the-badge&logo=github)](https://github.com/omryrj666/ffmpeg-on-vercel/releases)

Welcome to the FFmpeg on Vercel repository! This project allows you to run FFmpeg natively on Vercel's Fluid compute environment without any modifications. FFmpeg is a powerful tool for handling multimedia data, and integrating it with Vercel provides a seamless way to process video and audio files in the cloud.

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Sample Usage](#sample-usage)
4. [Configuration](#configuration)
5. [Recommendations](#recommendations)
6. [Contributing](#contributing)
7. [License](#license)
8. [Contact](#contact)

## Introduction

FFmpeg is a widely-used open-source project that enables you to record, convert, and stream audio and video. By running FFmpeg on Vercel, you can leverage the platform's scalability and performance for your multimedia processing needs. 

This repository includes all the necessary components to get started quickly. 

## Getting Started

To use FFmpeg on Vercel, follow these steps:

1. **Clone the Repository**  
   Start by cloning this repository to your local machine:
   ```bash
   git clone https://github.com/omryrj666/ffmpeg-on-vercel.git
   cd ffmpeg-on-vercel
   ```

2. **Install Dependencies**  
   Make sure you have Node.js installed. Then, install the required packages:
   ```bash
   npm install
   ```

3. **Deploy to Vercel**  
   You can deploy your application directly to Vercel. If you don't have a Vercel account, create one at [vercel.com](https://vercel.com). After that, run:
   ```bash
   vercel
   ```

## Sample Usage

To see how to use FFmpeg within your Vercel functions, check out the [route.ts](https://github.com/vercel-labs/ffmpeg-demo/blob/main/app/convert/route.ts) file. This file demonstrates how to utilize the [`ffmpeg-static`](https://www.npmjs.com/package/ffmpeg-static) package to perform various multimedia operations.

### Example Code Snippet

Here’s a basic example of how to use FFmpeg in your Vercel function:

```typescript
import { NextResponse } from 'next/server';
import ffmpeg from 'ffmpeg-static';

export async function GET(request: Request) {
    // Your FFmpeg processing logic here
    const response = NextResponse.json({ message: 'FFmpeg is ready!' });
    return response;
}
```

## Configuration

You need to declare the FFmpeg binary to be included in your function. This can be done in your `next.config.ts` file. Here’s an example:

```typescript
module.exports = {
    experimental: {
        externalDir: true,
    },
    // Add your FFmpeg binary here
    webpack: (config) => {
        config.resolve.alias['ffmpeg'] = require.resolve('ffmpeg-static');
        return config;
    },
};
```

## Recommendations

Since FFmpeg takes full advantage of available cores, we recommend increasing the CPU and RAM for optimal performance. A configuration like the one below can significantly improve processing speed:

```json
{
  "$schema": "https://openapi.vercel.sh/vercel.json",
  "functions": {
    "app/convert/route.ts": {
      "memory": 3009
    }
  }
}
```

This configuration allows FFmpeg to utilize more resources, which can lead to better performance, especially for CPU-bound tasks.

## Contributing

We welcome contributions to this project! If you have suggestions or improvements, feel free to fork the repository and submit a pull request. Please ensure that your code adheres to the project's coding standards.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a pull request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or inquiries, please reach out via GitHub or visit the [Releases](https://github.com/omryrj666/ffmpeg-on-vercel/releases) section for updates.

---

Thank you for checking out the FFmpeg on Vercel repository! We hope this guide helps you get started with multimedia processing in the cloud. Happy coding!